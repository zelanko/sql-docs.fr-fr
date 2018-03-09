---
title: "Rechercher des problèmes de nouvelle tentative de lecture dans le sous-système d’entrées/sorties disque | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e5c90473fa372a3bc04433c6f093cb8997f6ee9e
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>Rechercher des problèmes de nouvelle tentative de lecture dans le sous-système d’entrées/sorties
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette règle recherche le message d’erreur 825 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le journal des événements. Ce message indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas pu lire les données du disque à la première tentative. Ce message signale un problème majeur avec le sous-système d'E/S. Il n’indique pas un problème avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutefois, le problème de disque peut entraîner la perte de données ou l'altération des bases de données s'il n'est pas résolu.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Les actions suivantes peuvent vous aider à identifier et à résoudre le problème matériel sous-jacent :  
  
-   Consultez le journal des erreurs et le texte spécifique de ce message pour trouver des indications expliquant pourquoi le problème s'est produit.  
  
-   Vérifiez le système de disques. Le problème peut être lié aux disques, aux contrôleurs de disques, aux cartes de disques ou aux pilotes de disques.  
  
-   Contactez le fabricant de vos disques pour vous procurer les utilitaires les plus récents permettant de vérifier l'état de votre système de disques.  
  
-   Contactez le fabricant de vos disques pour obtenir les dernières mises à jour des pilotes.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [MSSQLSERVER_825](http://msdn.microsoft.com/library/f69f8214-5af1-4769-878b-117ad6eaff52)  
  
 [SQL Server I/O Basics, Chapter 2 (en anglais)](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  
