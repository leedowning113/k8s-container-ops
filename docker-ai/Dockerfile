FROM python:3.9-slim

#  작업 디렉터리 생성 및 이동
WORKDIR /app

#  AI 라이브러리 설치 (CPU 전용)
RUN pip install --no-cache-dir torch --index-url https://download.pytorch.org/whl/cpu
RUN pip install --no-cache-dir scikit-learn

# Python 스크립트 생성
RUN printf "import torch\n\
import time\n\
print('--- [A-Pod] AI Operation Test ---', flush=True)\n\
print(f'Engine: PyTorch {torch.__version__}', flush=True)\n\
a = torch.ones(1000, 1000)\n\
b = torch.ones(1000, 1000)\n\
res = torch.matmul(a, b)\n\
print(f'AI Math Test Result Shape: {res.shape}', flush=True)\n\
print('Status: AI Logic Running Successfully on CPU!', flush=True)\n\
while True:\n\
    print('AI pod alive:', time.ctime(), flush=True)\n\
    time.sleep(10)\n" > main.py

# Python unbuffered 모드
CMD ["python", "-u", "main.py"]

