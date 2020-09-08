# loadup

Header only library for NtLoadDriver and NtUnloadDriver. Registry entries and temp files that may be created are deleted when `driver::unload(...)` is called.

# examples

loading driver from buffer. `warning` please ensure ALL handles are closed to the driver before unloading the driver! `CloseHandle`!

```cpp
std::vector<std::uint8_t> drv_buffer(...);
const auto[result, reg_key] = driver::load(drv_buffer.data(), drv_buffer.size());
```

load driver from path on disk.

```cpp
auto result = driver::load("image.sys", "service_name");
```

unloading driver.

```cpp
auto result = driver::unload("service_name");
```
