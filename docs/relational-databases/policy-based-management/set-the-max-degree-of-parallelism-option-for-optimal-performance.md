---
title: Degré maximal de parallélisme et gestion basée sur des stratégies
description: Décrit la configuration d’une stratégie permettant de vérifier la valeur du degré maximal de parallélisme dans le cadre de la gestion basée sur des stratégies pour SQL Server.
ms.custom: seo-lt-2019
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a03a0236c177605bf5041e92ea9c19708d5bc9ae
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75776371"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Définir l'option max degree of parallelism pour des performances optimales
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle détermine si l'option max degree of parallelism (MAXDOP) (degré maximum de parallélisme) est définie sur une valeur supérieure à 8. La définition d'une valeur supérieure à 8 conduit souvent à la consommation inutile de ressources et à la dégradation des performances.  
  
## <a name="best-practice-recommendations"></a>Recommandations de bonnes pratiques  
 L’option de configuration max degree of parallelism (MAXDOP) contrôle le nombre de processeurs utilisés pour l’exécution d’une requête dans un plan parallèle. Cette option détermine le nombre de threads utilisés pour les opérateurs de plan de requête qui effectuent le travail en parallèle. Selon que SQL Server est configuré sur un ordinateur SMP (symmetric multiprocessing), un ordinateur NUMA (non-uniform memory access) ou des processeurs prenant en charge l’hyperthreading, vous devez configurer l’option max degree of parallelism en fonction. 
 
 Les recommandations pour configurer MAXDOP dépendent de la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée. Pour des instructions spécifiques à chaque version, consultez [Configurer l’option de configuration de serveur max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines) et configurez la stratégie pour vérifier la valeur de max degree of parallelism en conséquence.     
  
## <a name="for-more-information"></a>Informations supplémentaires  
 [Recommandations et instructions pour l’option de configuration max degree of parallelism dans SQL Server](https://go.microsoft.com/fwlink/?linkid=117786)    
 [Configurer l’option de configuration de serveur max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)     
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)     
  
