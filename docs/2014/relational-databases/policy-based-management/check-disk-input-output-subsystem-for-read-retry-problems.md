---
title: Rechercher les problèmes de nouvelle tentative de lecture dans le sous-système de sortie d’entrée de disque | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 19809b1554e435600eb4eeae424bed17dc27bdbb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85068991"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>Rechercher des problèmes de nouvelle tentative de lecture dans le sous-système d’E/S disque
  Cette règle recherche le message d'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 825 dans le journal des événements. Ce message indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'a pas pu lire les données du disque à la première tentative. Ce message signale un problème majeur avec le sous-système d'E/S. Il n’indique pas un problème avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutefois, le problème de disque peut entraîner la perte de données ou l'altération des bases de données s'il n'est pas résolu.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Les actions suivantes peuvent vous aider à identifier et à résoudre le problème matériel sous-jacent :  
  
-   Consultez le journal des erreurs et le texte spécifique de ce message pour trouver des indications expliquant pourquoi le problème s'est produit.  
  
-   Vérifiez le système de disques. Le problème peut être lié aux disques, aux contrôleurs de disques, aux cartes de disques ou aux pilotes de disques.  
  
-   Contactez le fabricant de vos disques pour vous procurer les utilitaires les plus récents permettant de vérifier l'état de votre système de disques.  
  
-   Contactez le fabricant de vos disques pour obtenir les dernières mises à jour des pilotes.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [MSSQLSERVER_825](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 [SQL Server I/O Basics, Chapter 2 (en anglais)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))  
  
  
