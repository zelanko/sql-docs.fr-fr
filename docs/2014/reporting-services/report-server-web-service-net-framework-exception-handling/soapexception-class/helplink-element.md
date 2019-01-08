---
title: HelpLink, élément | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- HelpLink element
- SoapException class
ms.assetid: a4489103-a874-44c2-8f75-95cb238928ed
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 26d75b623c9a3ca92b0d395e3ec4df47dd03418f
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53375261"
---
# <a name="helplink-element"></a>Élément HelpLink
  L’élément **HelpLink** de la propriété **Detail** est une chaîne d’URL générée par le serveur de rapports. L'URL cible une page Web gérée par le centre d'Aide et de support [!INCLUDE[msCoName](../../../includes/msconame-md.md)] et fournit une aide et des articles de base de connaissances supplémentaires sur les erreurs spécifiques qui se produisent dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. La syntaxe de l'URL est la suivante :  
  
 **http://** www.microsoft.com**/** produits**/** ee**/** transform.aspx **? EvtSrc**=_valeur_**& EvtID**=_valeur_**& ProdName** = _valeur_**& ProdVer**=_valeur_  
  
 Le tableau suivant répertorie les arguments de l’URL **HelpLink**.  
  
|Argument|Value|  
|--------------|-----------|  
|**EvtSrc**|"Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings"|  
|**EvtID**|Par exemple, rsReservedItem est le code d'erreur du serveur de rapports.|  
|**ProdName**|"Microsoft SQL%20Server%20Reporting%20Services." La valeur du nom de produit est encodée dans l'URL.|  
|**ProdVer**|Numéro de version de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. La valeur « 8.00 » signifie [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
 L’exemple suivant illustre la **HelpLink** URL retournée pour le code d’erreur `rsReservedItem`. Cette erreur se produit lorsqu'un utilisateur essaie de modifier ou supprimer un élément réservé dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] :  
  
```  
https://www.microsoft.com/products/ee/transform.aspx?  
EvtSrc=Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings  
&EvtID=rsReservedItem&ProdName=Microsoft%20SQL%20Server%20Reporting%20Services&ProdVer=8.00  
```  
  
 Vous pouvez accéder à l’élément **HelpLink** dans votre code à l’aide de la classe **SoapException**.  
  
```vb  
Try  
   rs.DeleteItem("/Report1")  
  
Catch e As SoapException  
   Console.WriteLine(e.Detail("HelpLink").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.DeleteItem("/Report1");  
}  
  
catch (SoapException e)  
{  
   Console.WriteLine(e.Detail["HelpLink"].InnerXml);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de la gestion des exceptions dans Reporting Services](../introducing-exception-handling-in-reporting-services.md)   
 [SoapException, classe Reporting Services](reporting-services-soapexception-class.md)   
 [Utilisation de la propriété des détails pour gérer des erreurs spécifiques](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
