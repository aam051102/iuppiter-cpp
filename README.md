# Iuppiter CPP
A nearly direct 1:1 port of the library Iuppiter, which allows for simple compression and decompression of text using the LZJB algorithm and Base64 encoding. It consists of a single header file with just a few functions.

NOTE: The actual implementation that I ported seems to have issues when the input is too short, so this probably has the same issue.

## Usage
```cpp
#include <iuppiter.h>

int main() {
    // Initialization - only done once
    Iuppiter::Init();

    std::string input = "To Be Encoded...";

    // To compressed byte array
    auto compressed = Iuppiter::Compress(Iuppiter::StringToByteArray(input));

    // To Base64
    auto base64 = Iuppiter::Base64::Encode(compressed);

    // Decoded byte array
    auto decoded = Iuppiter::Base64::Decode(Iuppiter::StringToByteArray(base64));

    // Decompressed string
    auto decompressed = Iuppiter::ByteArrayToString(Iuppiter::Decompress(decoded));

    // decompressed == input
}
```
