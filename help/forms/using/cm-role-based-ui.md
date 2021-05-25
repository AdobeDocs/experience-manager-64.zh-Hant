---
title: 在通信管理中不發佈基於角色的用戶介面
seo-title: 在通信管理中不發佈基於角色的用戶介面
description: 在通信管理中不發佈基於角色的用戶介面
seo-description: 在通信管理中不發佈基於角色的用戶介面
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: e077347bc202b6a411006032c68aa4a3152be7c5
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---


# 在通信管理{#do-not-publish-role-based-user-interface-in-correspondence-management}中不發佈基於角色的用戶介面

在AEM中，管理員可提供角色型存取權給不同的使用者群組，以對不同資源執行各種動作。 例如，建立或編輯資料字典的功能只能供特定使用者群組中的使用者使用，而其他使用者只能檢視和使用資料字典。

AEM介面會根據使用者的存取層級顯示選項，例如建立或編輯資產類型。 例如，如果使用者沒有建立資料字典的權限，則建立資料字典的選項不會出現在UI中。

雖然CRX可讓您設定使用者和群組帳戶的存取權限，但本文有關角色或使用者群組型存取權限。

有關組、權限、訪問控制清單以及管理用戶和組的詳細資訊，請參閱[用戶管理和安全性](/help/sites-administering/security.md)。

## 管理權限{#managing-permissions}

1. 確認您要為其管理權限的使用者已新增至相關使用者群組。

   例如，用戶John Doe被添加到組`agents`和`cm-creditcard`中。 如需詳細資訊，請參閱新增使用者或群組至群組。 如需詳細資訊，請參閱[管理使用者和使用者群組](/help/communities/users.md)。

   ![]()

1. 建立適合允許預定權限的資料夾。

   例如，如果企業有住房抵押、信用卡和保險部門，則可以建立名為`HomeMortgage`、`CreditCard,`和`Insurance`的資料夾，以保留相關資產，並僅為與其部門相關的資產選擇性地向代理商提供訪問權限。

1. 若要存取AEM WCM安全性，請執行下列其中一項操作：

   1. 在歡迎畫面或AEM中的各種位置中，按一下安全性圖示：

   1. 直接導覽至`https://[server]:[port]/useradmin`。 請務必以管理員身分登入AEM。

      ![]()
   左側樹列出系統中當前的所有用戶和組。 您可以選取要顯示的欄、排序欄的內容，甚至將欄標題拖曳到新位置，以變更欄的顯示順序。

   這些頁簽提供對各種配置的訪問：

1. 在左側樹狀清單中，點選兩下相關群組的名稱，然後選取「權限」標籤。

   若要找出群組名稱，您可以在提供的空間中輸入群組名稱。

1. 在權限標籤中，導覽至您要新增權限的路徑。 通信管理資料夾位於`content/apps/cm/`資料夾下。

   在「成員」列中，為要具有該路徑權限的成員選擇複選框。 清除要為刪除權限的成員的複選框。 在您對進行變更的儲存格中，會顯示紅色三角形。

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >資料夾中指定的權限會取代其子資料夾中指定的權限。

1. 點選「儲存」。
1. 步驟文字
1. 步驟文字
1. 步驟文字

