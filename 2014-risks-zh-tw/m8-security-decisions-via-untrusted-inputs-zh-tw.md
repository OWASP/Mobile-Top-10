---

layout: col-sidebar
title: "M8: 透過不受信任的輸入做出安全決策"
---

# 威脅主體

**應用層面 特定**

威脅主體包括可以將不受信任的輸入傳遞給敏感方法呼叫的實體。此類實體的範例包括但不限於使用者、惡意軟體和易受攻擊的應用程式。

# 攻擊媒介		

**利用難度 簡單**

有權存取應用程式的攻擊者可以攔截中介的呼叫並透過參數篡改來操縱結果。

# 安全層面的強度	

**普及性 常見** <br />
**偵測性 簡單**

開發人員通常使用隱藏欄位和數值或任何隱藏功能來區分較高層級的使用者和較低層級的使用者。攻擊者可以攔截呼叫（IPC 或 Web 服務呼叫）並修改此類敏感參數。此類功能的不佳執行會導致應用程式出現不當行為，甚至向攻擊者授予更高級別的權限。這可以透過掛鉤(hooking)功能輕鬆利用。 

# 技術性影響	

**影響程度 嚴重**

此漏洞可能會導致權限提升，從而為攻擊者提供更高權限和功能的存取權限。它甚至可以規避應用程式實施的安全機制，導致機密性和完整性喪失。

# 業務影響
	
**應用程式/業務 特定** 
		
此漏洞會導致聲譽損害。
同時，影響和損害完整性和保密性。

# 我是否容易受到「透過不受信任的輸入做出安全決策」的攻擊？

您的行動應用程式可以接受來自各種來源的數據。 在大多數情況下，這將是行程間通訊（IPC）機制。 一般來說，嘗試並遵守以下 IPC 設計模式：

- 如果有IPC通訊的業務需求，行動應用程式應限制只對可信任應用程式白名單的訪問
- 透過 IPC 入口點觸發的敏感操作在執行操作之前應要求使用者互動
- 從 IPC 入口點收到的所有輸入都必須經過嚴格的輸入驗證，以防止輸入驅動的攻擊
- 不要透過IPC機制傳遞任何敏感訊息，因為在某些情境下可能容易被第三方應用程式讀取

# 如何防止「透過不受信任的輸入做出安全決策」？

**對於 iOS 的舉例:**

- 請勿使用已棄用的 handleOpenURL 方法來處理URL架構呼叫。此方法不包含含有來源應用程式的 BundleID 的參數。
  - 相反的，使用 openURL:sourceApplication:annotation 方法並根據受信任應用程式的白名單驗證 sourceApplication 參數
- 不要使用 iOS 剪貼簿進行 IPC 通信，因為它很容易被裝置上的所有第三方應用程式設定或讀取。

**對於 Android 的舉例:**

- 無

# 攻擊情境舉例

無

# 參考資料

- [An In Depth Introduction to the Android Permissions Modeland How to Secure MultiComponent Applications](https://www.owasp.org/images/c/ca/ASDC12-An_InDepth_Introduction_to_the_Android_Permissions_Modeland_How_to_Secure_MultiComponent_Applications.pdf)