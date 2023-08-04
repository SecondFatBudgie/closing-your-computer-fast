from pynput import keyboard
import os

def on_press(key):
    # 检测按下的键是否符合快捷键组合
    if key == keyboard.Key.delete:
        # 设置一个标志来记录是否按下了Delete键
        global delete_pressed
        delete_pressed = True

    # 检测是否按下了1键，并且Delete键也被按下
    if key == keyboard.KeyCode.from_char('1') and delete_pressed:
        # 执行关机操作
        shutdown_computer()

def on_release(key):
    # 检测是否释放了Delete键
    if key == keyboard.Key.delete:
        # 重置标志
        global delete_pressed
        delete_pressed = False

def shutdown_computer():
    """立即关机计算机。"""
    if os.name == 'nt':  # Windows系统
        os.system('shutdown /s /t 0')
    else:
        print("不支持的操作系统。")

# 创建键盘监听器
listener = keyboard.Listener(on_press=on_press, on_release=on_release)

# 设置一个标志来记录是否按下了Delete键
delete_pressed = False

# 启动键盘监听器
listener.start()

# 进入监听状态，直到按下Ctrl+C退出程序
try:
    listener.join()
except KeyboardInterrupt:
    pass
