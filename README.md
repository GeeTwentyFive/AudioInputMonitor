# Usage:
```c
int AudioInputMonitor__Monitor(ma_format format, ma_uint32 channels, ma_uint32 sampleRate, AudioInputMonitor__DataCallback *OUT_dataCallback);
```
`format` is one of:
- `ma_format_u8`
- `ma_format_s16`
- `ma_format_s24`
- `ma_format_s32`
- `ma_format_f32`

Data callback prototype:
```c
void DataCallback(const void *pData, ma_uint32 frameCount)
```

# Example:
```c
void AudioInputCallback(const void *pData, ma_uint32 frameCount) {

        for (int i = 0; i < frameCount; i++) {
                printf("%hd\n", *(short*)pData);
        }

}
```
```c
if (!AudioInputMonitor__Monitor(ma_format_s16, 1, 48000, &AudioInputCallback)) {
        puts("ERROR: Failed to start monitoring audio input");
}
```
