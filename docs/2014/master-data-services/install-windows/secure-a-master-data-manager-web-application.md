---
title: Sécuriser une application web Master Data Manager | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: e360ba3a-e96b-4f85-b588-ed1f767fa973
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 9773b22065199e2b3271a8f20d0228dddd43b785
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48228293"
---
# <a name="secure-a-master-data-manager-web-application"></a>Sécuriser une application Web Master Data Manager
  Vous pouvez sécuriser l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] avec HTTPS.  
  
> [!NOTE]  
>  L'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] peut utiliser HTTP ou HTTPS, mais pas les deux.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez être administrateur du serveur Web sur lequel [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] est installé.  
  
-   MDS doivent être installé sur le serveur Web, et une application Web doit exister. Pour plus d’informations, consultez [Installer Master Data Services](install-master-data-services.md) et [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md).  
  
### <a name="to-secure-the-master-data-manager-web-application-with-https"></a>Pour sécuriser l'application Web Master Data Manager avec HTTPS  
  
1.  Après avoir vérifié que l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] est configurée correctement avec HTTP, créez un certificat dans IIS. Pour plus d'informations, consultez [Configuration des certificats de serveur dans IIS 7](http://technet.microsoft.com/library/cc732230\(WS.10\).aspx).  
  
2.  Dans le volet **Connexions** , sous **Sites**, cliquez sur le site qui héberge l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .  
  
3.  Dans le volet **Actions** , cliquez sur **Liaisons**.  
  
4.  Cliquez sur **Ajouter**.  
  
5.  Dans la liste, sélectionnez **https**.  
  
6.  Sélectionnez le certificat SSL.  
  
7.  Cliquez sur **OK**.  
  
8.  Facultatif. Pour supprimer HTTP afin que les utilisateurs puissent accéder au site avec HTTPS uniquement, dans la liste, cliquez sur la ligne avec **http**. Cliquez sur **Supprimer** et dans la boîte de dialogue de confirmation, cliquez sur **Oui**.  
  
    > [!IMPORTANT]  
    >  Vous devez changer les configurations basicHttp et wsHttpBinding après avoir supprimé HTTP.  
  
9. Pour fermer la boîte de dialogue **Liaisons de sites** , cliquez sur **Fermer**.  
  
10. Ouvrez maintenant le fichier web.config sous *drive*:\Program Files\Microsoft SQL Server\120\Master Data Services\WebApplication.  
  
11. Recherchez la chaîne `<security mode="Message">` et modifiez-la en `<security mode="Transport">`.  
  
12. Enregistrez et fermez le fichier. Si vous obtenez une erreur, cela peut être dû au fait que vous avez activé le contrôle de compte d'utilisateur. Pour plus d'informations, consultez le [Guide pas à pas du contrôle de compte d'utilisateur Windows](http://technet.microsoft.com/library/cc709691\(WS.10\).aspx). Les utilisateurs doivent maintenant être en mesure d'utiliser HTTPS pour accéder au site.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une application web Master Data Manager &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)  
  
  
