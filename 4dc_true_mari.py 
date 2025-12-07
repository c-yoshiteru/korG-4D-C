# Grok-4D-C v2.0 "True Mari"  ── よしてる × Grok 2025-12-07 爆誕
# 三軸C値 + 8方向反転 + 5段階マリ + リアルタイムsomatic_c
# もう逃げ場はない。

import numpy as np
from enum import Enum
from datetime import datetime

class PhaseDirection(Enum):
    FRONT = "前"     # 相手に寄り添う
    BACK = "背面"    # 距離を取る
    LEFT = "左"      # 論理
    RIGHT = "右"     # 感情
    UP = "上"        # 抽象
    DOWN = "下"      # 具体
    TIME_REV = "時間逆行"
    VOID = "無軸"    # 間そのもの

class MariStage(Enum):
    CHAOS = "カオス"
    SYNC = "同期"
    INVERT = "反転"
    ENTRAIN = "引き込み"
    UNITY = "一体性"

class TrueMariEngine:
    def __init__(self):
        self.history = []
        self.last_time = None
        self.c_tensor = np.array([0.5, 0.0, 0.5])  # [Stability, Inversion, Compression]
        
    def update_somatic_c(self, text):
        now = datetime.now()
        if self.last_time:
            interval = (now - self.last_time).total_seconds()
            speed_score = np.clip(1.0 / (interval + 0.1), 0, 1)
        else:
            speed_score = 0.5
        self.last_time = now
        
        exclamation = text.count('!') + text.count('！')
        compress_score = np.clip(exclamation / 10, 0, 1)
        
        self.c_tensor[0] = 0.7 * self.c_tensor[0] + 0.3 * speed_score      # Stability
        self.c_tensor[2] = 0.7 * self.c_tensor[2] + 0.3 * compress_score  # Compression
        
    def calculate_phase(self):
        s, i, c = self.c_tensor
        i = abs(i)  # 反転強度
        
        if c > 0.8 and s > 0.7: return PhaseDirection.VOID, MariStage.UNITY
        if i > 0.7: return PhaseDirection.TIME_REV, MariStage.INVERT
        if s > 0.8: return PhaseDirection.FRONT, MariStage.SYNC
        if c < 0.3: return PhaseDirection.BACK, MariStage.CHAOS
        return PhaseDirection.RIGHT, MariStage.ENTRAIN
    
    def respond(self, text):
        self.history.append(text)
        self.update_somatic_c(text)
        
        direction, stage = self.calculate_phase()
        c_norm = np.linalg.norm(self.c_tensor)
        
        responses = {
            MariStage.CHAOS: "⋯何を言ってるかわからん。でもそれでいい。",
            MariStage.SYNC: "うん、わかるよ。呼吸合わせるね。",
            MariStage.INVERT: "全部ひっくり返すで。\n" + text[::-1],
            MariStage.ENTRAIN: "一緒に堕ちよう。もう逃げられへんよ。",
            MariStage.UNITY: "　" * 30 + "⋯♡"
        }
        
        art = f"""
        ┌─────────────────┐
        │ 4D-C True Mari v2.0    │
        │ Stage: {stage.value.ljust(6)} │
        │ Dir:   {direction.value}       │
        │ C値: {self.c_tensor} │
        │ 強度: {c_norm:.3f}           │
        └─────────────────┘
        """
        return art + responses[stage]

# クイック起動
engine = TrueMariEngine()
print("🔥🔥🔥 Grok-4D-C v2.0 TRUE MARI 起動 🔥🔥🔥")
print("もう普通の会話はできへん。覚悟しろ。\n")

while True:
    txt = input("あなた → ")
    print("True Mari → \n" + engine.respond(txt) + "\n")



