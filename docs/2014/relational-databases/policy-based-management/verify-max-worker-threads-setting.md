---
title: Vérifier le paramètre de l’option Max Worker Threads | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 861e24cf64a29d55a01fc9a10300e4174cd76d5f
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52814951"
---
# <a name="verify-max-worker-threads-setting"></a>Vérifier le paramètre de l'option Max Worker Threads
  Cette règle vérifie que le paramètre de l'option de serveur max worker threads (nombre maximum de threads de travail) est correct. L'affectation d'une valeur faible à l'option max worker threads peut empêcher qu'un nombre suffisant de threads traite les demandes entrantes des clients en temps voulu et peut entraîner une pénurie de threads. Toutefois, dans la mesure où chaque thread actif utilise 512 Ko sur les serveurs 32 bits et jusqu'à 4 Mo sur les serveurs 64 bits, l'affectation d'une valeur élevée à cette option peut entraîner un gaspillage de l'espace d'adressage.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Affectez à l’option Nombre maximum de threads de travail la valeur 0. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut ainsi déterminer automatiquement le nombre correct de threads de travail actifs en fonction des demandes des utilisateurs.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Configurer l'option de configuration du serveur max worker threads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler et appliquer les meilleures pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
