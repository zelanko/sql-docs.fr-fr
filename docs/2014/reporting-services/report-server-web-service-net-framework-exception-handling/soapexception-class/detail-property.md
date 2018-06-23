---
title: Detail, propriété | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
caps.latest.revision: 32
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: fa7a39ee74bcdd9399c6e06eff9ee6df4688653a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041030"
---
# <a name="detail-property"></a>Propriété Detail
  La propriété **Detail** de la classe [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** possède la structure XML suivante :  
  
## <a name="elements"></a>Éléments  
 **Detail**  
 Élément de niveau supérieur qui contient tous les autres éléments de détail de l'erreur.  
  
 **ErrorCode**  
 Code d'erreur propre à [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 **HttpStatus**  
 Code d'état HTTP.  
  
 **Message**  
 Message d'erreur et code d'erreur attribués par le serveur de rapports.  
  
 **HelpLink**  
 URL du lien d'aide vers un site Web sur lequel des informations complémentaires sur l'erreur sont disponibles. Pour plus d’informations, consultez [HelpLink, élément](helplink-element.md).  
  
 **LinkID**  
 ID assigné au lien.  
  
 **ProductName**  
 Nom du produit. La valeur par défaut est **Microsoft SQL Server Reporting Services**.  
  
 **ProductVersion**  
 Version de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. La longueur maximale autorisée s'élève à 15 caractères. Le format du numéro de version doit être comme suit : 8.00.0xxx.00.  
  
 **ProductLocaleId**  
 ID des paramètres régionaux ou ID de la langue de la DLL INTL de l'application (par exemple, 0x41A).  
  
 **OperatingSystem**  
 Système d'exploitation sur lequel [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] est installé. Les valeurs valides incluent **0** pour un système d’exploitation indépendant, **1** pour [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)] et **16** pour Windows XP.  
  
 **CountryLocaleId**  
 ID des paramètres régionaux ou ID de la langue du système d'exploitation. Par exemple, la valeur de la version française de Windows est 0x040c.  
  
 **MoreInformation**  
 Chaîne XML qui contient des exceptions imbriquées qui se sont produites pendant l'exécution de la méthode.  
  
 **Source**  
 Élément enfant de **MoreInformation**. Source de l’erreur.  
  
 **Message**  
 Élément enfant de **MoreInformation**. Message d'erreur de l'exception imbriquée. Cet élément inclut des attributs XML pour **ErrorCode** et **HelpLink**.  
  
 **Avertissements**  
 Chaîne XML qui contient les avertissements retournés par le traitement des rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de la gestion des exceptions dans Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [SoapException, classe Reporting Services](reporting-services-soapexception-class.md)   
 [Utilisation de la propriété des détails pour gérer des erreurs spécifiques](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  