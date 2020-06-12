---
title: Sécuriser une application Web Master Data Manager
description: Dans SQL Server, vous pouvez sécuriser l’application Web principale Data Manager avec HTTPs. Vous devez être administrateur et MDS doit être installé sur le serveur Web.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c87fd72a7257615ab83a7e9845fdd4c6a80d70f7
ms.sourcegitcommit: 903856818acc657e5c42faa16d1c770aeb4e1d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83731582"
---
# <a name="secure-a-master-data-manager-web-application"></a>Sécuriser une application Web Master Data Manager

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Vous pouvez sécuriser l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] avec HTTPS.  
  
> [!NOTE]  
>  L'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] peut utiliser HTTP ou HTTPS, mais pas les deux.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez être administrateur du serveur Web sur lequel [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] est installé.  
  
-   MDS doivent être installé sur le serveur Web, et une application Web doit exister. Pour plus d’informations, consultez [Installer Master Data Services](../../master-data-services/install-windows/install-master-data-services.md) et [Créer une application Web Master Data Manager &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md).  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>Pour sécuriser l'application Web Master Data Manager avec HTTPS  
  
1.  Après avoir vérifié que l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] est configurée correctement avec HTTP, créez un certificat dans IIS. Pour plus d'informations, consultez [Configuration des certificats de serveur dans IIS 7](https://technet.microsoft.com/library/cc732230\(WS.10\).aspx).  
  
2.  Dans le volet **Connexions** , sous **Sites**, cliquez sur le site qui héberge l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
3.  Dans le volet **Actions**, cliquez sur **Liaisons**.  
  
4.  Cliquez sur **Add**.  
  
5.  Dans la liste, sélectionnez **https**.  
  
6.  Sélectionnez le certificat TLS/SSL.  
  
7.  Cliquez sur **OK**.  
  
8.  facultatif. Pour supprimer HTTP afin que les utilisateurs puissent accéder au site avec HTTPS uniquement, dans la liste, cliquez sur la ligne avec **http**. Cliquez sur **Supprimer** et dans la boîte de dialogue de confirmation, cliquez sur **Oui**.  
  
    > [!IMPORTANT]  
    >  Vous devez changer les configurations basicHttp et wsHttpBinding après avoir supprimé HTTP.  
  
9. Pour fermer la boîte de dialogue **Liaisons de sites** , cliquez sur **Fermer**.  
  
10. Ouvrez maintenant le fichier web.config sous *lecteur*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication.  
  
11. Recherchez la chaîne `<security mode="Message">` et modifiez-la en `<security mode="Transport">`.  

12. Remplacez `<serviceMetadata httpGetEnable="true" httpsGetEnabled="false">` par `<serviceMetadata httpGetEnable="false" httpsGetEnabled="true">` afin d’éviter les problèmes susceptibles d’apparaître dans le client Silverlight.

13. Enregistrez et fermez le fichier. Si vous obtenez une erreur, cela peut être dû au fait que vous avez activé le contrôle de compte d'utilisateur. Les utilisateurs doivent maintenant être en mesure d'utiliser HTTPS pour accéder au site.  

  
## <a name="see-also"></a>Voir aussi  
 [Créer une application web Master Data Manager &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  
