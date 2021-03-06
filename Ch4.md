
# 第四章 Transient Response暫態響應

- [第四章 Transient Response暫態響應](#第四章-transient-response暫態響應)
  - [簡單的意義](#簡單的意義)
  - [4.2 極點、零點 與 系統響應](#42-極點零點-與-系統響應)
    - [極點](#極點)
    - [零點](#零點)
    - [Ex. 求轉移函數$\frac{s-2}{s(s+5)}$](#ex-求轉移函數fracs-2ss5)
    - [Ex. 求輸出響應](#ex-求輸出響應)
    - [極點(poles)/零點(zeros)在系統響應中的規律](#極點poles零點zeros在系統響應中的規律)
  - [4.3 一階系統](#43-一階系統)
    - [響應時間有三種標準](#響應時間有三種標準)
      - [***Time constant時間常數***](#time-constant時間常數)
      - [***Rise time上升時間$T_r$***](#rise-time上升時間t_r)
      - [***Settling time安定時間$T_s$***](#settling-time安定時間t_s)
    - [整理](#整理)
    - [一階系統單位步階響應的特徵](#一階系統單位步階響應的特徵)
    - [系統鑑別](#系統鑑別)
  - [4.4 二階系統](#44-二階系統)

## 簡單的意義  

1. 系統響應就是輸出，系統響應 = 自然響應 + 強制響應
2. 強制響應才是我們期望系統該有的輸出
3. 自然響應是系統本身必然產生的輸出，是我們希望盡量避免的，所以越快衰減到 $0$ 越好


## 4.2 極點、零點 與 系統響應

|                 |       |                 |       |                  |
| :-------------: | :---: | :-------------: | :---: | :--------------: |
|  系統輸出響應   |   =   |    強制響應     |   +   |     自然響應     |
| System Response |   =   | Forced Response |   +   | Natural Response |

極點、零點都是頻域平面中 $s$ 變數的值(含實部虛部)  

### 極點

函數的極點定義：$\begin{array}{l} 1.此點代入函數，將算出無窮大 \\ 2.此點為函數分母的根(即使此根可與分子約分) \end{array}$  

### 零點

函數的零點定義：$\begin{array}{l} 1.此點代入函數，將算出\ 0 \\ 2.此點為函數分子的根(即使此根可與分母約分) \end{array}$

-------------------------------------------------------------------------------------------------------------------------------------------------------

### Ex. 求轉移函數$\frac{s-2}{s(s+5)}$

Poles(極點): $0,-5$  
Zeros(零點): $2$

-------------------------------------------------------------------------------------------------------------------------------------------------------

### Ex. 求輸出響應

![Figure4.1(a)](pics/ch4/Figure4.1_a.png)  

$C(s) = G(s)R(s) = \frac{s+2}{s(s+5)} = \frac{a_1}{s+5}+\frac{a_2}{s}$  
$\Rightarrow C(s) = \frac{\frac{3}{5}}{s+5} + \frac{\frac{2}{5}}{s}$  
$\xrightarrow{\mathcal{L^{-1}}}c(t) = \frac{3}{5}e^{-5t}+\frac{2}{5}e^{0t}$ (輸出響應)  
其中  
$\frac{3}{5}e^{-5t}$ 稱為***自然響應***(因為輸出型式為$e$)， $-5$ 來自轉移函數 $G(s)$ 的極點pole($s = -5$)  
$\frac{2}{5}e^{0t}$ 稱為***強制響應***(因為是外部輸入在影響的，好像強迫系統輸出一樣)，$0$ 來自輸入函數 $R(s)$ 的極點  

可以歸納出  
$輸出響應 = 自然響應 + 強制響應$  

-------------------------------------------------------------------------------------------------------------------------------------------------------

### 極點(poles)/零點(zeros)在系統響應中的規律

1. 輸出響應 $=$ 自然響應 + 強制響應
2. 轉移函數的極點產生自然響應(記得轉移函數代表***系統本身的行為***)
3. 輸入函數的極點產生強制響應
4. 當自然響應衰減至 $0$ 以後，輸出就只剩下強制響應(外部輸入造成的部分)
5. ***轉移函數***在實部上的極點 ($s = -\alpha + j0$) 會產生 $e^{-\alpha t}$ 形式的輸出，由此可知，極點越左邊(越負)，***自然響應***會越快衰減至 $0$
6. 零點(zero)的作用  
   若 輸入$=\frac{1}{s-2}$，轉移函數$=\frac{s-2}{s+1}$，輸出$=$？  
   按照上面Ex的方法計算  
   $C(s) = \frac{1}{s-2}\times\frac{s-2}{s+1}$  
   $\Rightarrow C(s) = \frac{1}{s+1}$  
   $\xrightarrow{\mathcal{L^{-1}}}c(t) = e^{-1t}$  
   輸出只剩自然響應 $e^{-1t}$  
   強制響應 $e^{2t}$ 在計算過程中分子分母相消不見  
   $\Rightarrow$ 當我們把***轉移函數的零點***作為輸入時，輸出只會有自然響應，而自然響應會隨著時間衰減至$0$，變成 $0$ 輸出  
   $\Rightarrow$ 對系統輸入***零點***就不輸出  
   $\Rightarrow$ 轉移函數的零點***阻擋***特定的輸入
7. 暫時不懂

-------------------------------------------------------------------------------------------------------------------------------------------------------

## 4.3 一階系統

舉例一個不帶零點的一階系統 $G(s) = \frac{a}{s+a}, a \gt 0$  
並給定單位步階輸入 $R(s) = \frac{1}{s}$  
$\Rightarrow C(s) = R(s)G(s) = \frac{a}{s(s+a)} = \frac{1}{s}-\frac{1}{s+a}$  
$\xrightarrow{\mathcal{L^{-1}}} c(t)=1-e^{-at}$  
則 $1$ 為強制響應  
而 $-e^{-at}$ 為自然響應  
當 $t\rightarrow\infty$ 時，$-e^{-at}$ 會衰減至 $0$，只剩下強制響應 $1$，這也被稱為***穩態值***  

自然響應衰減至 $0$ 後達到***穩態***  
我們想知道達到穩態需要多少時間，也就是***響應時間***  

實際上需要無限多時間，但這不切實際，所以訂定標準，只要自然響應衰減到符合標準，就假裝系統已經達到穩態  

-------------------------------------------------------------------------------------------------------------------------------------------------------

### 響應時間有三種標準

-------------------------------------------------------------------------------------------------------------------------------------------------------

#### ***Time constant時間常數***

1. 自然響應衰減到初始的 $37\%$ 所需要的時間
2. 步階響應提升到 $63\%$ 所需要的時間

用1.求時間常數  
初始 $t=0$ $e^{-at} \Rightarrow e^{-a0} = 1$  
$37\%$自然響應$=0.37 = e^{-at}$  
$-at = \ln{0.37}\approx -1$  
$\Rightarrow -1 = -at$  
$\Rightarrow t=\frac{1}{a}$

用2.求時間常數  
$100\%$步階響應$=1-0=1$  
$63\%$步階響應$0.63=c(t)=1-e^{-at}$  
$\Rightarrow e^{-at}=0.37$  
$\Rightarrow t=\frac{1}{a}$  

-------------------------------------------------------------------------------------------------------------------------------------------------------

#### ***Rise time上升時間$T_r$***

輸出波型從$10\%$穩態值上升到$90\%$穩態值所需要的時間
$100\%$步階響應$=1-0=1$  
$90\%$步階響應$0.9=c(t)=1-e^{-at}$  
$\Rightarrow e^{-at}=0.1$  
$\Rightarrow -at = \ln{0.1}\approx -2.31$  
$\Rightarrow t=\frac{2.31}{a}$  
$10\%$步階響應$0.1=c(t)=1-e^{-at}$  
$\Rightarrow e^{-at}=0.9$  
$\Rightarrow -at = \ln{0.9}\approx -0.11$  
$\Rightarrow t=\frac{0.11}{a}$  
$T_r=\frac{2.31}{a}-\frac{0.11}{a}$  
$T_r=\frac{2.2}{a}$

-------------------------------------------------------------------------------------------------------------------------------------------------------

#### ***Settling time安定時間$T_s$***

達到$98\%$穩態值所需要的時間  

$100\%$步階響應$=1-0=1$  
$98\%$步階響應$0.98=c(t)=1-e^{-at}$  
$\Rightarrow e^{-at}=0.02$  
$\Rightarrow -at = \ln{0.02}\approx -4$  
$\Rightarrow t=\frac{4}{a}$  
$-at=-4$  
$t=\frac{4}{a}$  
$T_s=\frac{4}{a}$

-------------------------------------------------------------------------------------------------------------------------------------------------------

### 整理

$time\ constant=\frac{1}{a}$  
$T_r=\frac{2.2}{a}$  
$T_s=\frac{4}{a}$  

### 一階系統單位步階響應的特徵

1. 不會overshoot (超過穩態值)
2. 非零的初始斜率
3. $a$ 是唯一會影響暫態響應的參數，跟自然響應類似，$a$ 作為極點，越左邊(越負)，暫態響應越快衰減至 $0$

### 系統鑑別

給一個黑盒子系統  
意思就是，我們可以給這個系統輸入，也可以偵測輸出  
但不知道內部元件結構(也就是不知道轉移函數$G(s)$)  

假設我們測量該系統的單位步階響應如圖  
![Figure4.6](pics/ch4/Figure4.6.png)  

那麼理應可以根據測量結果推算出系統的轉移函數  

考慮一個簡單的一階系統，$G(s)=\frac{k}{s+a}$  
其步階響應為  
$C(s)=\frac{k}{s(s+a)}=\frac{\frac{k}{a}}{s}-\frac{\frac{k}{a}}{s+a}$  
$\Rightarrow c(t) = \frac{k}{a}e^{0t}-\frac{k}{a}e^{-at}$  
從測量圖中可以看出穩態值$c(\infin)=0.72\Rightarrow\frac{k}{a}=0.72$  
Time constant:  
$63\%\times c(\infin)\approx 0.45$  
直接看測量圖$c(t)=0.45$對應$t\approx 0.13$  
time constant $\approx 0.13$  
$\because t=\frac{1}{a}$  
$a\approx 7.7$  
$\frac{k}{a}=0.72 \Rightarrow k\approx 5.54$  
那麼就可以以此推論出轉移函數  
$G(s)=\frac{5.54}{s+7.7}$

## 4.4 二階系統

|          | 改變參數造成的影響 |
| :------- | :----------------- |
| 一階系統 | 響應***速度***     |
| 二階系統 | 響應***波型***     |

二階系統的單位步階響應***通式***  
$R(s)=\frac{1}{s}\rightarrow\frac{b}{s^2+as+b}\rightarrow C(s)\xrightarrow{\mathcal{L^{-1}}} c(t)=\begin{cases} k_1+k_2e^{\lambda_1t}+k_3e^{\lambda_2t}\ 轉移函數分母具相異實根 \\ k_1+k_2e^{\lambda t}+k_3e^{\lambda t}\ \ \ \ 轉移函數分母具相同實根 \end{cases}$  
其中 $\lambda_i$ 就是轉移函數的極點  

>前提：阻尼的意義  
>>類似於緩衝器、避震器的功能  
>>能量不夠(低於穩定值)就提供能量  
>>能量太多(高於穩定值)就吸收能量  
>
>運用此特性使系統的能量***盡快趨近於穩定***

常見的4種二階系統  

|          |                                                                 |      |
| :------- | :-------------------------------------------------------------- | :--- |
| 過阻尼   | $R(s)=\frac{1}{s}\rightarrow\frac{9}{s^2+9s+9}\rightarrow C(s)$ |      |
| 欠阻尼   | $R(s)=\frac{1}{s}\rightarrow\frac{9}{s^2+2s+9}\rightarrow C(s)$ |      |
| 無阻尼   | $R(s)=\frac{1}{s}\rightarrow\frac{9}{s^2+9}\rightarrow C(s)$    |      |
| 臨界阻尼 | $R(s)=\frac{1}{s}\rightarrow\frac{9}{s^2+6s+9}\rightarrow C(s)$ |      |

極點的實部代表響應的指數衰減(越負衰減越快)  
極點的虛部代表震盪頻率(絕對值越大)

過阻尼：阻尼太高的時候，會在前期吸收太多能量，以至於較慢達到穩態  
欠阻尼：阻尼不夠的時候，會 高過穩態->低過穩態->反覆進行  
臨界阻尼：阻尼恰到好處，能以最快的速度趨近於穩態  
這邊找到一個相當好懂的示意圖  
![阻尼解說](https://highscope.ch.ntu.edu.tw/wordpress/wp-content/uploads/2014/12/Fig-2-Damped-Swinging-Doors-Animation.gif)  
