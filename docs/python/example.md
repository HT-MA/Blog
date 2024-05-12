以下是一个简单的 Python 脚本示例，它用于读取一个文本文件的内容并输出到标准输出：

```python
import sys

def main():
    # 检查是否提供了文件名作为命令行参数
    if len(sys.argv) < 2:
        print("Usage: python script.py <filename>")
        sys.exit(1)
    
    # 获取文件名
    filename = sys.argv[1]
    
    try:
        # 读取文件内容
        with open(filename, 'r') as file:
            content = file.read()
            # 输出文件内容到标准输出
            print("File content:")
            print(content)
    except FileNotFoundError:
        print(f"Error: File '{filename}' not found.")
        sys.exit(1)
    except Exception as e:
        print(f"Error reading file: {e}")
        sys.exit(1)

if __name__ == "__main__":
    main()
```

这个脚本接受一个文件名作为命令行参数，并读取该文件的内容，然后将内容输出到标准输出。你可以将上面的代码保存到一个名为 `script.py` 的文件中，并使用 `python script.py <filename>` 命令来执行，其中 `<filename>` 是你要读取的文本文件的路径。

这个脚本处理了一些可能出现的错误，如文件不存在或读取文件时出现异常，并向用户显示相应的错误消息。