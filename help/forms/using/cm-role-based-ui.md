---
title: 在通信管理中不發佈基於角色的用戶介面
seo-title: DO NOT PUBLISH Role based user interface in Correspondence Management
description: 在通信管理中不發佈基於角色的用戶介面
seo-description: DO NOT PUBLISH Role based user interface in Correspondence Management
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# 在通信管理中不發佈基於角色的用戶介面 {#do-not-publish-role-based-user-interface-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

在AEM中，管理員可提供角色型存取權給不同的使用者群組，以對不同資源執行各種動作。 例如，建立或編輯資料字典的功能只能供特定使用者群組中的使用者使用，而其他使用者只能檢視和使用資料字典。

AEM介面會根據使用者的存取層級顯示選項，例如建立或編輯資產類型。 例如，如果使用者沒有建立資料字典的權限，則建立資料字典的選項不會出現在UI中。

雖然CRX可讓您設定使用者和群組帳戶的存取權限，但本文有關角色或使用者群組型存取權限。

如需群組、權限、存取控制清單及管理使用者和群組的詳細資訊，請參閱 [使用者管理與安全性](/help/sites-administering/security.md).

## 管理權限 {#managing-permissions}

1. 確認您要為其管理權限的使用者已新增至相關使用者群組。

   例如，使用者John Doe會新增至群組 `agents` 和 `cm-creditcard`. 如需詳細資訊，請參閱新增使用者或群組至群組。 如需詳細資訊，請參閱 [管理使用者和使用者群組](/help/communities/users.md).

   ![]()

1. 建立適合允許預定權限的資料夾。

   例如，如果企業有住房抵押、信用卡和保險部門，則可以建立名為 `HomeMortgage`, `CreditCard,`和 `Insurance` 保留相關資產，並有選擇地讓代理人獲取與其部門有關的資產。

1. 若要存取AEM WCM安全性，請執行下列其中一項操作：

   1. 在歡迎畫面或AEM中的各種位置中，按一下安全性圖示：

   1. 直接導覽至 `https://[server]:[port]/useradmin`. 請務必以管理員身分登入AEM。

      ![]()
   左側樹列出系統中當前的所有用戶和組。 您可以選取要顯示的欄、排序欄的內容，甚至將欄標題拖曳到新位置，以變更欄的顯示順序。

   索引標籤可供存取各種設定：

1. 在左側樹狀清單中，點選兩下相關群組的名稱，然後選取「權限」標籤。

   若要找出群組名稱，您可以在提供的空間中輸入群組名稱。

1. 在權限標籤中，導覽至您要新增權限的路徑。 通信管理資料夾位於 `content/apps/cm/` 檔案夾。

   在「成員」列中，為要具有該路徑權限的成員選擇複選框。 清除要為刪除權限的成員的複選框。 在您對進行變更的儲存格中，會顯示紅色三角形。

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >資料夾中指定的權限會取代其子資料夾中指定的權限。

1. 點選「儲存」。
1. 步驟文字
1. 步驟文字
1. 步驟文字

