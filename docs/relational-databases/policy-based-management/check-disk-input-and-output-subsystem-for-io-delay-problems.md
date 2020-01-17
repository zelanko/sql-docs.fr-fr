---
title: Rechercher les problèmes de délai d’E/S dans le sous-système d’E/S disque
description: Découvrez comment activer une stratégie permettant de détecter les problèmes de délai d’E/S dans le sous-système d’E/S disque en recherchant dans le journal des événements le message d’erreur 833 lié à la gestion basée sur des stratégies avec SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0cf1dc8196ef8e248da485b01efc4bf192d4248c
ms.sourcegitcommit: 035ad9197cb9799852ed705432740ad52e0a256d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75558170"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a>Rechercher des problèmes de délai d’E/S dans le sous-système d’E/S disque
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle recherche le message d'erreur 833 dans le journal des événements. Ce message indique que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a émis une demande de lecture ou d'écriture à partir du disque et que la demande a mis plus de 15 secondes à retourner un résultat. Cette erreur est signalée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et indique un problème avec le sous-système d'E/S disque. Des délais de cette importance peuvent sévèrement nuire aux performances de votre environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Essayez de résoudre le problème en recherchant dans le journal des événements système d'éventuels messages d'erreur liés au matériel. Examinez également les journaux spécifiques au matériel s'ils sont disponibles.  
  
 Utilisez l'Analyseur de performances pour consulter les compteurs suivants :  
  
-   Moy. disque s/transfert  
  
-   Longueur moyenne de la file d'attente du disque  
  
-   Longueur actuelle de la file d'attente du disque  
  
 Par exemple, la Moy. disque s/transfert sur un ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est généralement inférieure à 15 millisecondes. Si la valeur Moy. disque s/transfert augmente, cela indique que le sous-système d'E/S disque ne parvient pas parfaitement à suivre la demande d'E/S.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
   
  
 [Article 897284 de la Base de connaissances Microsoft](https://go.microsoft.com/fwlink/?linkid=117743)  
  
 [SQL Server I/O Basics, Chapter 2 (en anglais)](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))
