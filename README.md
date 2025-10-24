# SORD_M68_USB_Keyboard_Converter_USB_IF

## Summary

このコードは、USBキーボード変換機において、USBキーボードを接続する側にあるpico2のファームウェアです。
USB HIDを用いて、キーコードを取得し、UART1経由でもう一つのpico2に転送します。

Firmware for the Pico 2 board that handles the USB keyboard connection in the adapter.
This firmware acquires keycodes using USB HID and transmits them to the other Pico 2 via UART1.

