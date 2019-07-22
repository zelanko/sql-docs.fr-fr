---
title: Groupes de disponibilité de base pour une base de données
description: 'Décrit les différences entre les groupes de disponibilité Always On normaux et les groupes de disponibilité Always On de base ainsi que la configuration d’un groupe de disponibilité de base. '
ms.custom: seodec18
ms.date: 02/01/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 285adbc7-ac9b-40f6-b4a9-3f1591d3b632
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46630e36db03d55c8e90be64570975e42466fbba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67991359"
---
# <a name="basic-always-on-availability-groups-for-a-single-database"></a>Groupes de disponibilité Always On de base pour une base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Les groupes de disponibilité Always On de base fournissent une solution haute disponibilité pour SQL Server 2016 et SQL Server 2017 Standard Edition. Un groupe de disponibilité de base prend en charge un environnement de basculement pour une base de données unique. Il est créé et géré davantage comme les [Groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) classiques (avancés) avec Enterprise Edition. Les différences et limitations des groupes de disponibilité de base sont résumées dans ce document.  
  
## <a name="features"></a>Fonctionnalités  
 Les groupes de disponibilité Always On de base remplacent la fonctionnalité de mise en miroir de bases de données déconseillée et fournissent un niveau de prise en charge des fonctionnalités similaire. Les groupes de disponibilité de base permettent à une base de données principale de conserver un réplica unique. Ce réplica peut utiliser le mode de validation synchrone ou asynchrone. Pour plus d’informations sur les modes de disponibilité, consultez [Modes de disponibilité &#40;groupes de disponibilité Always On&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md). Le réplica secondaire reste inactif, à moins qu’un basculement soit requis. Ce basculement inverse les affectations de rôle principal et secondaire, ce qui implique la transformation du réplica secondaire en base de données active principale. Pour plus d’informations sur le basculement, consultez [Basculement et modes de basculement &#40;groupes de disponibilité Always On&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md). Les groupes de disponibilité de base peuvent fonctionner dans un environnement hybride qui s’étend sur site et couvre Microsoft Azure.  
  
## <a name="limitations"></a>Limitations  
 Les groupes de disponibilité de base utilisent un sous-ensemble de fonctionnalités si on les compare aux groupes de disponibilité avancés sur SQL Server 2016 Enterprise Edition. Les groupes de disponibilité de base incluent les limitations suivantes :  
  
- Limite de deux réplicas (principal et secondaire). Les groupes de disponibilité de base pour SQL Server 2017 sur Linux prennent en charge un seul réplica de configuration supplémentaire.
  
- Aucun accès en lecture sur le réplica secondaire.  
  
- Aucune sauvegarde sur le réplica secondaire.  

- Aucune vérification de l’intégrité sur les réplicas secondaires. 

- Aucune prise en charge des réplicas hébergés sur les serveurs exécutant une version de SQL Server antérieure à SQL Server 2016 Community Technology Preview 3 (CTP3).  

- Prise en charge d’une base de données de disponibilité.  
  
- Mise à niveau de groupes de disponibilité de base vers des groupes de disponibilité avancés impossible. Le groupe doit être supprimé et rajouté à un groupe qui contient des serveurs exécutant uniquement SQL Server 2016 Enterprise Edition.  
  
- Les groupes de disponibilité de base sont pris en charge uniquement pour les serveurs Standard Edition. 

- Les groupes de disponibilité de base ne peuvent pas faire partie d’un groupe de disponibilité distribué. 
  
## <a name="configuration"></a>Configuration  
 Un groupe de disponibilité de base Always On peut être créé sur deux serveurs SQL Server 2016 Standard Edition. Lorsque vous créez un groupe de disponibilité de base, vous devez spécifier les deux réplicas lors de la création.  
  
 Pour créer un groupe de disponibilité de base, utilisez la commande transact-SQL **CREATE AVAILABILITY GROUP** et spécifiez l’option **WITH BASIC** (la valeur par défaut étant **ADVANCED**). Vous pouvez également créer le groupe de disponibilité de base à l’aide de l’interface utilisateur dans SQL Server Management Studio à partir de la version 17.8. Pour plus d’informations, consultez [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md). 
  
> [!NOTE]  
>  Les limitations des groupes de disponibilité de base s’appliquent à la commande **CREATE AVAILABILITY GROUP** lorsque **WITH BASIC** est spécifiée. Par exemple, vous obtiendrez une erreur si vous essayez de créer un groupe de disponibilité de base qui permet un accès en lecture. Les autres limitations s’appliquent de la même manière. Reportez-vous à la section Limitations de cette rubrique pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
