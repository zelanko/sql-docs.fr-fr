---
title: Quoi de neuf dans l’intégration CLR ( Microsoft Docs
description: Microsoft SQL Server hébergeant CLR s’appelle l’intégration CLR. Cet article décrit de nouvelles fonctionnalités dans l’intégration CLR dans SQL Server 2012.
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: d27bf0d925d3a98dda488fb85aff7446434cc8ad
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488088"
---
# <a name="clr-integration---what39s-new"></a>Intégration CLR - Qu’est-ce&#39;nouveau
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Voici les nouvelles fonctionnalités apportées à l'intégration du CLR dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] :  
  
-   Dans la version 4 du CLR, les objets de base de données CLR n'interceptent plus des exceptions d'état endommagées. Ces exceptions sont maintenant interceptées dans l'intégration du CLR qui héberge la couche. Ces exceptions peuvent encore être prises par les composants de la base de données CLR en définissant un attribut de code[\<(héritageCorruptedStateExceptionsPolicy> Element](https://go.microsoft.com/fwlink/?LinkId=204954)). Toutefois, cette opération n'est pas recommandée car les résultats ne sont pas fiables lorsqu'une exception d'état endommagée se produit.  
  
-   En raison des strictes conditions de sécurité de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les composants de base de données CLR continueront à utiliser le modèle de sécurité d'accès du code défini dans la version 2.0 du CLR.  
  
-   Dans la version CLR 4, une erreur de format dans une valeur **System.TimeSpan** générera un **System.FormatExceptions**. Avant la version 4 du CLR, une erreur de format dans une valeur **System.TimeSpan** a été ignorée. Les applications de base de données qui s’appuient sur le comportement avant la version 4 du CLR doivent s’exécuter avec un niveau de compatibilité de base de données (niveau de**compatibilité ALTER DATABASE**) de 100 ou moins. Pour plus d’informations, voir [<TimeSpan_LegacyFormatMode> Element](https://go.microsoft.com/fwlink/?LinkId=205109).  
  
-   La version 4 du CLR prend en charge Unicode 5.1. Les opérations de tri qui impliquent des accents et des symboles vont faire l'objet d'améliorations. Des problèmes de compatibilité peuvent survenir si votre application s'appuie sur un comportement de tri hérité. Pour permettre le tri de l’héritage, le niveau de compatibilité de la base de données **(niveau de compatibilité ALTER DATABASE**) doit être réglé à 100 ou moins. Pour prendre en charge cette fonctionnalité, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installe sort00001000.dll dans le répertoire du .NET Framework 4 (C:\Windows\Microsoft.NET\Framework\v4.0.30319). Pour plus d’informations, voir [ \<CompatSortNLSVersion> Element](https://go.microsoft.com/fwlink/?LinkId=205110).  
  
-   Les colonnes suivantes ont été ajoutées à [sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **total_processor_time_ms**, **total_allocated_memory_kb**et **survived_memory_kb**.  
  
  
