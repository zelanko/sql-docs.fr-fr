---
title: Définir l’option max degree of parallelism pour des performances optimales | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
manager: craigg
ms.openlocfilehash: 10187162bec9286867c56def5c8bc2b4c1ed5382
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51655618"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>Définir l'option max degree of parallelism pour des performances optimales
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle détermine si l'option max degree of parallelism (MAXDOP) (degré maximum de parallélisme) est définie sur une valeur supérieure à 8. La définition d'une valeur supérieure à 8 conduit souvent à la consommation inutile de ressources et à la dégradation des performances.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Définissez l'option max degree of parallelism sur 8 ou une valeur supérieure à l'aide de sp_configure.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Article 329204 de la Base de connaissances Microsoft](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [Configurer l'option de configuration du serveur Degré maximal de parallélisme](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
