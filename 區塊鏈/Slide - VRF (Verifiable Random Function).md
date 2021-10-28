# VRF (Verifiable Random Function)

## 可驗證的隨機函數

---

## 抽籤應用

---

![](https://i.imgur.com/a3QMuKj.png)

在 ADA, MATIC 上這類擁有 POS 機制的幣，都有利用到 VRF，來合理的隨機選出 Leader 與 Committee。

---

## 在區塊鏈上取得隨機數的難點

---

通常在計算機上（例如在遊戲應用程式中）所說的「隨機數」實際上是「偽隨機」的。

---

也就是說，它們依賴於使用者或其他型別的 Oracle（預言機）提供的足夠隨機的種子，例如氣象站的大氣噪聲、你的心律，它都可以從中產生一系列看似隨機的數字。「但是給定相同的種子，將容易產生不夠隨機的數字」。

---

並且需要驗證此隨機是不是合理的，在分散式的系統中，不同節點獲得隨機數後，不能輕易相信，必須要有一個方案能得知此隨機數沒有造假。

---

所以必須有兩點要滿足：

1. 擁有足夠隨機的種子來產生隨機數
2. 能夠驗證隨機數沒有造假可能

---

## VRF 如何滿足此需求？

我們擁有以下參數：

- X: 隨機種子
- PK: 公開金鑰
- SK: 私密金鑰

---

計算後會產生:

- Y: 偽隨機(pseudorandom)亂數
- ⍴: 可驗證亂數的證明

---

VRF 提供以下兩個函數:

- Evaluate(SK, X) → (Y, ⍴). 產生亂數：輸入私鑰 SK, 訊息 X ，輸出 pseudorandom output string Y 以及 proof ⍴.
- Verify(PK, X, Y, ⍴) → 0/1. 驗證亂數：輸入公鑰 PK, 訊息 X, 亂數 Y,以及 the proof ⍴. 若該亂數確實是由該公鑰對應之私鑰使用 Evaluate 函示所產生，則回傳 1 (true)

---

而 X 這個隨機種子，會以「上一輪的隨機值」與「slot number」為主，再加上「私鑰」，能夠產生足夠亂的數字。

---

slot 可以想像成區塊鏈的時鐘機制，由於區塊鏈是分散式系統，我們很難準確的說明 slot number 是多少。

---

![](https://i.imgur.com/RQWrry7.png)

詳細概念，以 MATIC 的 POS 來說，需以 epoch 與 slot 來表達整個系統的時間。時隙（slots）是時間的離散單位，長度為六秒。每個時隙可以包含一個塊，但也可以不包含一個塊。時隙構成了時期（epochs）—— 在 Polkadot 上，2400 個時隙構成了一個時期，即每個時期為 4 小時。

---

## 在 Solana 上的應用

---

彩票系統：設定一個數字，並說明可以大於還是小於彩票，並開獎

![](https://i.imgur.com/NYYrvsa.png)

---

https://devpost.com/software/solavip#updates

https://www.youtube.com/watch?v=5UNZhAKvL3c

---

原理：

Solana 的 slot 有 blockHashes 的設計，當玩家在當前 slot 下注完後，以此 slot 與使用者的私鑰做 VRF

---

驗證：

如果玩家對抽獎的隨機數感到不合理，可以找尋此下注的 transaction，並用此 slot 配合使用者公鑰來驗證隨機數是否合理

---

![](https://i.imgur.com/U1LlWOI.png)

---

## POS 應用 - Algorand 演算法

---

傳統的 BTF(拜占庭容錯協議)會知道下一個 Leader 是誰，這導致有被攻擊的可能性(e.g. DDOS，賄賂之類)

---

Algorand 為了解決這種潛在的風險，利用 VRF 來掩蓋 Leader Selection 的步驟。可以想像成：一般的 BFT 在每一輪開始時公平公開選出 Leader 以及 Committee，Algorand 則是像在每一輪開始時公布中獎號碼，每個使用者都可以自己拿自己的票根對獎，中獎的人即可成為下一輪的 Leader(或是 Committee Verifier)

---

![](https://i.imgur.com/idq5Fro.png)

---

1. 利用此區塊鏈系統的一個共同亂數種子，如果是上方舉例就是利用 slot
2. 每一個使用者都可以透過 Evaluate()，由自己的私鑰配合 VRF 來檢驗自己有沒有資格成為 Leader 或是委員會的成員(此資格通常是看算出來的亂數符不符合特定規則)
3. 如果發現自己有符合規則，則認定自己是 Leader，並發布區塊與 proof(如果有多個 Leader 則透過 hash 來去選擇誰 prioroty 最高)
4. 其他有疑問的人可以以 proof 來驗證抽籤結果

---

由於在得知誰是 Leader 時，此時已經發布了區塊，攻擊者為時已晚，無法進行攻擊
