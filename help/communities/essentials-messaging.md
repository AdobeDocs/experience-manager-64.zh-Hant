---
title: Messaging Essentials
seo-title: Messaging Essentials
description: 傳訊元件概觀
seo-description: Messaging component overview
uuid: 53711f4d-6bbc-4be9-aefe-4e75a81cd67f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: eb8fd2b3-0a31-425e-b0f1-38f09e1106df
exl-id: c6ad3c2b-8776-4ec4-99da-ab73ecc61153
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 3%

---

# Messaging Essentials {#messaging-essentials}

>[!CAUTION]
>
>AEM 6.4已結束延伸支援，本檔案不再更新。 如需詳細資訊，請參閱 [技術支援期](https://helpx.adobe.com//tw/support/programs/eol-matrix.html). 尋找支援的版本 [此處](https://experienceleague.adobe.com/docs/).

本頁面記錄使用傳訊元件以在網站上包含傳訊功能的詳細資訊。

## 用戶端的要點 {#essentials-for-client-side}

**撰寫訊息**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>社交/傳訊/元件/hbs/組合訊息</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>範本</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/composemessage.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>cs</strong></td> 
   <td>/libs/social/messaging/components/hbs/composemessage/clientlibs/composemessage.css</td> 
  </tr> 
  <tr> 
   <td><strong>屬性</strong></td> 
   <td>請參閱 <a href="configure-messaging.md">設定傳訊</a></td> 
  </tr> 
  <tr> 
   <td><strong>管理組態</strong></td> 
   <td><a href="messaging.md">設定傳訊</a></td> 
  </tr> 
 </tbody> 
</table>

**訊息清單** （用於收件匣、已傳送和清除）

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td><p>社交/傳訊/元件/hbs/messagebox</p> </td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientllibs</strong></a></td> 
   <td><p>cq.social.hbs.messaging</p> </td> 
  </tr> 
  <tr> 
   <td> <strong>範本</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/messagebox.hbs</td> 
  </tr> 
  <tr> 
   <td><strong>cs</strong></td> 
   <td>/libs/social/messaging/components/hbs/messagebox/clientlibs/messagebox.css</td> 
  </tr> 
  <tr> 
   <td><strong>屬性</strong></td> 
   <td>請參閱 <a href="configure-messaging.md">設定傳訊</a></td> 
  </tr> 
  <tr> 
   <td><strong>管理組態</strong></td> 
   <td><a href="messaging.md">設定傳訊</a></td> 
  </tr> 
 </tbody> 
</table>

另請參閱 [用戶端自訂](client-customize.md)

## 伺服器端的Essentials {#essentials-for-server-side}

* [設定傳訊](configure-messaging.md)

* [傳訊用戶端API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/api/package-summary.html) 用於SCF元件

* [傳訊API](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/api/package-summary.html) 服務

* [傳訊端點](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/messaging/client/endpoints/package-summary.html)

* [伺服器端自訂](server-customize.md)

>[!CAUTION]
>
>字串參數必須*不*包含下列MessageBuilder方法的尾隨斜線「/」：
>
>* `setInboxPath`()
>* `setSentItemsPath`()
>
>例如：
>
>
```
>valid: mb.setInboxPath( "/mail/inbox" );
> not valid: mb.setInboxPath( "/mail/inbox/" );
>```

### 社群網站 {#community-site}

使用精靈建立的社群網站結構會在選取時包含傳訊功能。 請參閱 `User Management` 設定 [社群網站主控台](sites-console.md#user-management).

### 程式碼範例：收到的消息通知 {#sample-code-message-received-notification}

社交訊息功能會擲回操作事件，例如 `send`, `marking read`, `marking delete`. 您可以擷取這些事件，並對事件中包含的資料採取動作。

以下範例為事件處理常式，其偵聽 `message sent` 事件，並使用 `Day CQ Mail Service`.

若要試用伺服器端範例指令碼，您需要開發環境和建立OSGi套件組合的功能。

1. 以管理員身分登入 ` [CRXDE|Lite](http://localhost:4502/crx/de)`
1. 建立 `bundle node`in `/apps/engage/install` 具有任意名稱，例如

   * **[!UICONTROL 符號名稱]**:com.engage.media.social.messaging.MessagingNotification
   * **[!UICONTROL 名稱]**:快速入門教學課程訊息通知
   * **[!UICONTROL 說明]**:當使用者收到訊息時傳送電子郵件通知的範例服務
   * **[!UICONTROL 套件]**: `com.engage.media.social.messaging.notification`

1. 瀏覽到 `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/src/main/java/com/engage/media/social/messaging/notification`

   1. 刪除 `Activator.java` 自動建立的類
   1. 建立類 `MessageEventHandler.java`
   1. 將下方的程式碼複製/貼到 `MessageEventHandler.java`

1. 按一下 **[!UICONTROL 全部儲存]**
1. 導覽至 `/apps/engage/install/com.engage.media.social.messaging.MessagingNotification/com.engage.media.social.messaging.MessagingNotification.bnd` 並按照 `MessageEventHandler.java` 程式碼。
1. 建立套件組合
1. 確保 `Day CQ Mail Service`已配置OSGi服務
1. 以示範使用者身分登入，並傳送電子郵件給其他使用者
1. 收件者應會收到有關新訊息的電子郵件

#### MessageEventHandler.java {#messageeventhandler-java}

```java
package com.engage.media.social.messaging.notification;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;
import org.apache.sling.api.resource.ResourceResolver;
import org.apache.sling.api.resource.ResourceResolverFactory;
import org.apache.sling.api.resource.Resource;
import org.apache.commons.mail.Email;
import org.apache.commons.mail.EmailException;
import org.apache.commons.mail.SimpleEmail;
import org.apache.commons.mail.HtmlEmail;
import java.util.List;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import com.adobe.cq.social.messaging.api.Message;
import com.adobe.cq.social.messaging.api.MessagingEvent;
import com.day.cq.mailer.MessageGatewayService;
import com.day.cq.mailer.MessageGateway;

@Component(immediate=true)
@Service(EventHandler.class)
@Properties({
        @Property(name = "event.topics", value = "com/adobe/cq/social/message")
})
public class MessagingEventHandler implements EventHandler {
    private Logger logger = LoggerFactory.getLogger(MessagingEventHandler.class);

    @Reference
    ResourceResolverFactory resourceResolverFactory;

    @Reference
    private MessageGatewayService messageGatewayService;

    ResourceResolver resourceResolver=null;
    MessageGateway messageGateway=null;

    public void sendMail(String from, String to,String subject, String content){
        Email email = new SimpleEmail();
        messageGateway = messageGatewayService.getGateway(SimpleEmail.class);
        try {
         email.addTo(to);
            email.addReplyTo(from);
            email.setFrom(from);
            email.setMsg(content);
            email.setSubject(subject);
         messageGateway.send(email);
        } catch(EmailException ex) {
            logger.error("MessageNotificaiton : Error sending email : "+ex.getMessage());
        }
        logger.info("**** MessageNotification **** Mail sent to " + to);
    }

    public void handleEvent(Event event) {
        //Get Message Path and originator User's ID from event
        String messagePath = (String) event.getProperty("path");
        String senderId = (String) event.getProperty("userId");
        MessagingEvent.MessagingActions action = (MessagingEvent.MessagingActions) event.getProperty("action");
        try{
            if(MessagingEvent.MessagingActions.MessageSent.equals(action)){
                resourceResolver = resourceResolverFactory.getAdministrativeResourceResolver(null);

                //Read message
                Resource resource = resourceResolver.getResource(messagePath);
                Message msg = resource.adaptTo(Message.class);

                //Get list of recipient Ids from message
                //For Getting Started Tutorial, Id is same as email. If that is not the case in your site, 
                //an additional step is needed to retrieve the email for the Id
                List<String> reclist = msg.getRecipientIdList();
                for(int i=0;i<reclist.size();i++){
                    //Send Email using Mailing Service
                    sendMail("admin@cqadmin.qqq",reclist.get(i),"New message on Getting Started Tutorial", "Hi\nYou have received a new message from  " +  senderId + ". To read it, sign in to Getting Started Tutorial.\n\n-Engage Admin");
                }
            }
        } catch(Exception ex){
            logger.error("Error getting message info : " + ex.getMessage());
        } finally {
            resourceResolver.close();
        }

    }
}
```
