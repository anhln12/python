Hôm nay nhận được yêu cầu của dự án là phải làm cách nào bảo vệ được được source code, chống sao chép source code. Qua quá trình tìm hiểu, mình thấy sử dụng Cython khá là ổn, không những bảo vệ được source code của Python mà còn tăng hiệu suất xử lý nhờ được build thành 1 thư viện C và load vào HDH

Cython là gì?
Cython là ngôn ngữ lập trình nhằm trở thành siêu ngôn ngữ (superset) của ngôn ngữ lập trình Python. Nó được thiết kế để đạt được hiệu năng giống như C với mã được viết chủ yếu bằng Python với cú pháp lấy cảm hứng từ C bổ sung sang.

- Phát triển bởi Robert Bradshaw, Stefan Behnel, et al.
- Phát hành lần đầu vào 28/07/2007
- Repository: github.com/cython/cython
- Viết bằng Python, C
- Loại: Programming language
- License: Apache License 2.0
- Website: cython.org

Cài đặt Cython Module

Để cài đặt Cython Module, chúng ta sử dụng trình quản lý module của Python là PIP cho Python 2 hoặc PIP3 cho Python 3
```
pip install cython
```

Tạo project Cython

Một chương trình Cython tối thiểu có 3 files:

- Python source code: là các file chứa mã nguồn của Python sẽ được compile thành 1 Cython Extension
- 1 file setup.py sử dụng module setuptools của Python để tạo Cython Extension
- 1 file main để import Cython Extension

Một ví dụ về chương trình mà mình sẽ tạo ra có tên là VinaSupportModule có 3 files như sau:

![image](https://github.com/user-attachments/assets/4d50f2dc-a799-4740-a34d-ad9518b5f59c)

+ File: my-module.py chứa mã nguồn của chương trình Python:
```
def hello_world():
    print('We are vinasupport.com Team')
```
+ File: setup.py
```
from distutils.core import Extension, setup
from Cython.Build import cythonize
# define an extension that will be cythonized and compiled
ext = Extension(name="VinaSupportModule", sources=["my-module.py"])
setup(ext_modules=cythonize(ext))
```
+ File: main.py
```
import VinaSupportModule
VinaSupportModule.hello_world()
```

Compile Extension

Sử dụng command sau để compile source Python thành 1 extension
```
python setup.py build_ext --inplace
```

Sau khi build chúng ta có 1 extension có tên là: VinaSupportModule.cpython-35m-x86_64-linux-gnu.so

Giờ copy nó vào thư viện của hệ điều hành (Trên máy mình là Ubuntu 18.04)
```
sudo cp VinaSupportModule.cpython-35m-x86_64-linux-gnu.so /usr/lib/x86_64-linux-gnu/
```
Test Extension

Như đã nói ở trên, chúng ta import module vào trong source file main.py và chạy file main.py để kiểm tra xem module mà chúng ta đã tạo ra có hoạt động đúng không.
```
python main.py
```


