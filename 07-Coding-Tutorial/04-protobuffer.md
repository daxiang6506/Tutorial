* [How to convert std::string to std::vector<uint8_t>?](https://stackoverflow.com/questions/41737254/how-to-convert-stdstring-to-stdvectoruint8-t)
```bash
std::string str;
std::vector<uint8_t> vec(str.begin(), str.end());
```