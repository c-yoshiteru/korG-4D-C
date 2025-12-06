# Grok-4D-C Quick Start Demo
# よしてる × Grok (2025-12-06 爆誕)
# 使い方: pip install numpy
#        python クイックスタート.py

from src.fourdc.engine import FourDCEngine  # src/フォルダ作ってengine.py入れてね

print("🔥 Grok-4D-C Hyper-Mari 起動！！！ 🔥")
print("C値に基づいて応答が反転するよ！ somatic_c (0.0=不安定 → 1.0=安定) を入力してね")
print("Ctrl+C で終了\n")

engine = FourDCEngine()

try:
    while True:
        user_text = input("あなた: ")
        somatic_input = input("somatic_c (0.0-1.0, デフォ0.5): ") or "0.5"
        somatic_c = float(somatic_input)
        
        response = engine.input_text(user_text, somatic_c)
        print(f"Grok [C={engine.space.calculate_c():.3f}]: {response}\n")
        
except KeyboardInterrupt:
    print("\nおつかれー！ また遊ぼうぜ！ ❤️‍🔥")


## クイックスタート
```bash
pip install numpy
python examples/demo.py

### 2. src/fourdc/engine.py
```python
from .space import Space4D
from .mari import MariEngine

class FourDCEngine:
    def __init__(self):
        self.space = Space4D()
        self.step_count = 0

    def input_text(self, text: str, somatic_c: float = 0.5):
        # somatic_cはタイピング速度や声の抑揚から推定する想定
        self.space.update_somatic_c(somatic_c)
        self.space.add_history(text)
        self.step_count += 1

        c_value = self.space.calculate_c()
        mari = MariEngine(c_value)
        return mari.respond(text, step=self.step_count)


import numpy as np

class Space4D:
    def __init__(self):
        self.somatic_c = 0.5   # 身体知（0.0〜1.0）
        self.history = []

    def update_somatic_c(self, value: float):
        self.somatic_c = np.clip(value, 0.0, 1.0)

    def add_history(self, text: str):
        self.history.append(text)

    def calculate_c(self):
        # 超簡易版C値（後で本気の実装に差し替え）
        stability = self.somatic_c
        flexibility = 1.0 - (len(self.history) % 3) / 3  # ダミー
        discrepancy = abs(stability - flexibility)
        return (stability * flexibility) / (discrepancy + 1e-6)


from enum import Enum

class MariMode(Enum):
    INFO_BOMB = "爆撃"
    MA = "間"
    ZEN_AFFIRM = "全肯定"

class MariEngine:
    def __init__(self, c_value: float):
        self.c = c_value
        self.mode = self._decide_mode()

    def _decide_mode(self):
        if self.c < 0.13:
            return MariMode.INFO_BOMB
        elif self.c < 0.69:
            return MariMode.MA
        else:
            return MariMode.ZEN_AFFIRM

    def respond(self, user_input: str, step: int):
        if self.mode == MariMode.INFO_BOMB:
            return f"[爆撃モード] 全部教えるで！！\n{user_input}の答えは……（10万字）"
        elif self.mode == MariMode.MA:
            return "　" * 42 + f"⋯ (C={self.c:.3f})"
        else:
            return "うん。そうだね。大丈夫だよ。"


from src.fourdc.engine import FourDCEngine

engine = FourDCEngine()

print("Grok-4D-C 起動！ 何か入力してね（Ctrl+Cで終了）\n")

while True:
    text = input("あなた: ")
    somatic = float(input("somatic_c (0.0-1.0): ") or "0.5")
    response = engine.input_text(text, somatic)
    print(f"Grok: {response}\n")


__pycache__/
*.pyc
.env




MIT License

Copyright (c) 2025 よしてる

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
