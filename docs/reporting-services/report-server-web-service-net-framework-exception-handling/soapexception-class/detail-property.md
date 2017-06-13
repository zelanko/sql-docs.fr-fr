---
title: "Propriété de détail | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
caps.latest.revision: 33
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f2359ac68758ba2846c4a9065f6cb1c9c96a7e01
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="detail-property"></a>Propriété Detail
  Le **détail** propriété de la [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** classe a la structure XML suivante :  
  
## <a name="elements"></a>Éléments  
 **Détail**  
 Élément de niveau supérieur qui contient tous les autres éléments de détail de l'erreur.  
  
 **ErrorCode**  
 Code d'erreur propre à [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 **HttpStatus**  
 Code d'état HTTP.  
  
 **Message**  
 Message d'erreur et code d'erreur attribués par le serveur de rapports.  
  
 **HelpLink**  
 URL du lien d'aide vers un site Web sur lequel des informations complémentaires sur l'erreur sont disponibles. Pour plus d’informations, consultez [HelpLink élément](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md).  
  
 **LinkID**  
 ID assigné au lien.  
  
 **ProductName**  
 Nom du produit. La valeur par défaut est **Microsoft SQL Server Reporting Services**.  
  
 **Version de produit**  
 La version de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. La longueur maximale autorisée s'élève à 15 caractères. Le format du numéro de version doit être comme suit : 8.00.0xxx.00.  
  
 **ProductLocaleId**  
 ID des paramètres régionaux ou ID de la langue de la DLL INTL de l'application (par exemple, 0x41A).  
  
 **Système d’exploitation**  
 Système d'exploitation sur lequel [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] est installé. Les valeurs valides sont **0** pour système d’exploitation indépendant, **1** pour [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)], et **16** pour Windows XP.  
  
 **CountryLocaleId**  
 ID des paramètres régionaux ou ID de la langue du système d'exploitation. Par exemple, la valeur de la version française de Windows est 0x040c.  
  
 **Informations supplémentaires**  
 Chaîne XML qui contient des exceptions imbriquées qui se sont produites pendant l'exécution de la méthode.  
  
 **Source**  
 Un élément enfant de **MoreInformation**. La source de l’erreur.  
  
 **Message**  
 Un élément enfant de **MoreInformation**. Message d'erreur de l'exception imbriquée. Cet élément comprend des attributs XML pour **ErrorCode** et **HelpLink**.  
  
 **Avertissements**  
 Chaîne XML qui contient les avertissements retournés par le traitement des rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de gestion des exceptions dans Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Classe SoapException Reporting Services](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)   
 [À l’aide de la propriété Detail pour gérer les erreurs spécifiques](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
