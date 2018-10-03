---
title: Ce que&#39;nouveauté d’intégration du CLR | Microsoft Docs
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b2adfc4b32b2d6223f2852a425bf073f14cb3294
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659344"
---
# <a name="clr-integration---what39s-new"></a>Intégration du CLR - ce que&#39;s nouveau
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Voici les nouvelles fonctionnalités apportées à l'intégration du CLR dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] :  
  
-   Dans la version 4 du CLR, les objets de base de données CLR n'interceptent plus des exceptions d'état endommagées. Ces exceptions sont maintenant interceptées dans l'intégration du CLR qui héberge la couche. Ces exceptions peuvent toujours être interceptées par les composants de base de données CLR en définissant un attribut de code ([\<legacyCorruptedStateExceptionsPolicy > élément](http://go.microsoft.com/fwlink/?LinkId=204954)). Toutefois, cette opération n'est pas recommandée car les résultats ne sont pas fiables lorsqu'une exception d'état endommagée se produit.  
  
-   En raison des strictes conditions de sécurité de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les composants de base de données CLR continueront à utiliser le modèle de sécurité d'accès du code défini dans la version 2.0 du CLR.  
  
-   Dans la version CLR 4, une erreur de format dans un **System.TimeSpan** valeur générera un **System.FormatExceptions**. Avant la version 4 du CLR, une erreur de format dans un **System.TimeSpan** valeur a été ignorée. Les applications de base de données qui reposent sur le comportement antérieur à la version 4 du CLR doivent s’exécuter avec un niveau de compatibilité de base de données (**ALTER DATABASE Compatibility Level**) inférieure ou égale à 100. Pour plus d’informations, consultez [< TimeSpan_LegacyFormatMode > élément](http://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   La version 4 du CLR prend en charge Unicode 5.1. Les opérations de tri qui impliquent des accents et des symboles vont faire l'objet d'améliorations. Des problèmes de compatibilité peuvent survenir si votre application s'appuie sur un comportement de tri hérité. Pour activer le tri, le niveau de compatibilité de base de données hérité (**ALTER DATABASE Compatibility Level**) doit être définie sur 100 ou inférieur. Pour prendre en charge cette fonctionnalité, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installe sort00001000.dll dans le répertoire du .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Pour plus d’informations, consultez [ \<CompatSortNLSVersion > élément](http://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Les colonnes suivantes ont été ajoutées à [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **total_processor_time_ms**, **total_allocated_memory_kb**, et **survived_ memory_kb**.  
  
  
