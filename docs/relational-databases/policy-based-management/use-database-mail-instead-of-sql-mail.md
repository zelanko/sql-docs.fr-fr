---
title: Utiliser la messagerie de base de données plutôt que SQL Mail | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: b08df7be-d8be-4184-a661-38ec0ac85cd1
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: c029883591c49c1be52d23a025ff522b4095a6f5
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68069151"
---
# <a name="use-database-mail-instead-of-sql-mail"></a>Utiliser la messagerie de base de données plutôt que SQL Mail
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle vérifie dans l'affichage catalogue sys.configurations si l'option de configuration au niveau serveur sqlmail XPs est définie sur ON.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 SQL Mail sera supprimé dans une version ultérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Pour envoyer du courrier, utilisez la messagerie de base de données.  
  
 SQL Mail s'exécute dans un processus interne à un service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si SQL Mail arrête de fonctionner, il en sera de même pour le serveur. La messagerie de base de données s'exécute en dehors de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un processus distinct, est évolutive et ne requiert pas l'installation des composants clients MAPI étendus sur le serveur de production.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les bonnes pratiques à l’aide de la gestion basée sur des stratégies](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
