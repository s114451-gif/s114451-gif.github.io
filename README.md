import random

def lunch_tarot():
    print("🔮 =================================== 🔮")
    print("       歡迎來到「今天吃什麼」午餐命運占卜      ")
    print("🔮 =================================== 🔮\n")
    
    # 🌟 請在這裡自由修改或增加你公司/家裡附近的餐廳口袋名單！
    lunch_pool = {
        "台式便當/乾麵": {"soup": False, "rice": True, "heavy": False},
        "日式拉麵": {"soup": True, "rice": False, "heavy": True},
        "熱騰騰的小火鍋": {"soup": True, "rice": True, "heavy": True},
        "健康水煮餐盒": {"soup": False, "rice": True, "heavy": False},
        "義大利麵/披薩": {"soup": False, "rice": False, "heavy": True},
        "麥當勞/肯德基炸雞": {"soup": False, "rice": False, "heavy": True},
        "福利社簡單吃": {"soup": False, "rice": False, "heavy": False},
        "牛肉麵/水餃": {"soup": True, "rice": False, "heavy": False},
    }

    # 1. 開始問問題（二選一，過濾條件）
    print("🛸 請依據你現在的「靈魂飢餓感」，回答以下三個問題：\n")
    
    # 問題一：想不想喝湯？
    ans1 = input("Q1: 今天想喝熱湯，還是吃乾的？ (1) 想要有湯 (2) 不要湯，乾的就好\n> ")
    want_soup = True if ans1 == "1" else False
    
    # 問題二：主食想要飯嗎？
    ans2 = input("\nQ2: 主食想要吃飯，還是麵食/其他？ (1) 要吃飯 (2) 吃麵或其它澱粉\n> ")
    want_rice = True if ans2 == "1" else False

    # 問題三：想吃重口味還是清淡？
    ans3 = input("\nQ3: 想吃邪惡重口味，還是清淡健康點？ (1) 越邪惡越好 (2) 偏向清淡\n> ")
    want_heavy = True if ans3 == "1" else False

    # 2. 根據回答過濾餐廳
    candidates = []
    for name, features in lunch_pool.items():
        # 如果符合大部分條件，就加入候選清單
        score = 0
        if features["soup"] == want_soup: score += 1
        if features["rice"] == want_rice: score += 1
        if features["heavy"] == want_heavy: score += 1
        
        # 只要滿足 2 個以上的條件，就列入考慮
        if score >= 2:
            candidates.append(name)

    # 如果沒半個符合（通常不會），就從全部裡面盲抽
    if not candidates:
        candidates = list(lunch_pool.keys())

    # 3. 命運抽獎
    print("\n🔮 正在感應你的胃壁細胞...")
    print("🎲 命運之輪開始旋轉...")
    
    final_choice = random.choice(candidates)
    
    print("\n✨ ================= 占卜結果 ================= ✨")
    print(f"🎯 宇宙指引你的午餐首選：【 {final_choice} 】")
    print("=================================================\n")
    print("祝你用餐愉快！不要再猶豫了，快去訂餐吧 😋")

if __name__ == "__main__":
    lunch_tarot()
