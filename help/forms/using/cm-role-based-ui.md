---
title: 在通信管理中不發佈基於角色的用戶介面
seo-title: 在通信管理中不發佈基於角色的用戶介面
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---


# 在Correponsent Management {#do-not-publish-role-based-user-interface-in-correspondence-management}中不要發佈基於角色的用戶介面

在AEM中，管理員可以針對不同的使用者群組提供以角色為基礎的存取權，以便對不同的資源執行各種動作。 例如，建立或編輯資料字典的功能只能供特定使用者群組中的使用者使用，而其他使用者只能檢視和使用資料字典。

AEM介面會根據使用者的存取層級，顯示選項，例如建立或編輯資產類型。 例如，如果使用者沒有建立資料字典的權限，則建立資料字典的選項不會顯示在UI中。

雖然CRX可讓您設定使用者和群組帳戶的存取權限，但本文內容是關於角色或使用者群組的存取權限。

有關組、權限、訪問控制清單以及管理用戶和組的詳細資訊，請參閱[用戶管理和安全](/help/sites-administering/security.md)。

## 管理權限{#managing-permissions}

1. 請確定您要管理權限的使用者已新增至相關使用者群組。

   例如，將用戶John Doe添加到組`agents`和`cm-creditcard`。 如需詳細資訊，請參閱新增使用者或群組至群組。 如需詳細資訊，請參閱[管理使用者和使用者群組](/help/communities/users.md)。

   ![]()

1. 建立適合允許所需權限的檔案夾。

   例如，如果企業有住房抵押、信用卡和保險部門，則可以建立名為`HomeMortgage`、`CreditCard,`和`Insurance`的資料夾來保存相關資產，並有選擇地為代理商訪問與其部門有關的資產。

1. 若要存取AEM WCM安全性，請執行下列其中一項作業：

   1. 從「歡迎」畫面或AEM中的各種位置，按一下安全性圖示：

   1. 直接導覽至`https://[server]:[port]/useradmin`。 請確定您以管理員身分登入AEM。

      ![]()
   左樹列出系統中當前的所有用戶和組。 您可以選取要顯示的欄、排序欄的內容，甚至將欄標題拖曳至新位置，以變更欄的顯示順序。

   這些頁籤可訪問各種配置：

1. 在左側樹狀結構清單中，點選兩下相關群組的名稱，然後選取「權限」標籤。

   要查找組的名稱，可以在提供的空間中鍵入組的名稱。

1. 在權限標籤中，導覽至您要新增權限的路徑。 The Corresponcess Management folders are under the `content/apps/cm/` folder.

   在「成員」列中，為要具有該路徑權限的成員選擇複選框。 清除要移除權限的成員的複選框。 在您所做變更的儲存格中，會出現紅色三角形。

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >在資料夾中指定的權限會取代其子資料夾中指定的權限。

1. 點選「儲存」。
1. 步驟文字
1. 步驟文字
1. 步驟文字

