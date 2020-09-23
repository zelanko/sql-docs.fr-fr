---
title: Utiliser des stratégies de groupe pour l’intégrité des groupes de disponibilité
description: Découvrez comment afficher les stratégies système des groupes de disponibilité qui sont utilisées par le tableau de bord Always On pour fournir des informations sur l’intégrité d’un groupe de disponibilité.
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: how-to
ms.assetid: 26bf8f71-c2b8-45ef-b3a3-372b96c9e6e3
author: rothja
ms.author: jroth
ms.openlocfilehash: 19eb6e3c43ce404770d641bc33bf663ad12a4b61
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91115825"
---
# <a name="evaluate-health-of-the-always-on-availability-group-using-group-policies"></a>Évaluer l’intégrité du groupe de disponibilité Always On à l’aide de stratégies de groupe
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Les stratégies système des groupes de disponibilité Always On sont utilisées par le tableau de bord Always On pour fournir des informations sur l’intégrité d’un groupe de disponibilité à l’utilisateur. Elles sont très utiles pour la résolution initiale des problèmes opérationnels affectant un groupe de disponibilité. Vous pouvez étendre ces stratégies et les utiliser pour personnaliser le tableau de bord Always On ou les exécuter instantanément pour générer les informations d’intégrité désirées.  
  
 Il existe 14 stratégies système pour les groupes de disponibilité. Pour plus d’informations sur chaque stratégie, consultez [Stratégies Always On pour les problèmes opérationnels avec des groupes de disponibilité Always On (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
## <a name="view-or-evaluate-availability-groups-system-policies"></a>Afficher ou évaluer les stratégies système des groupes de disponibilité  
 Pour afficher ou exécuter les stratégies système des groupes de disponibilité dans SSMS (SQL Server Management Studio), effectuez les étapes suivantes :  
  
1.  Dans **l’Explorateur d’objets**, développez **Gestion**, **Gestion de la stratégie**, **Stratégies**, puis **Stratégies système**.  
  
2.  Cliquez avec le bouton droit sur l’une des stratégies, puis cliquez sur **Évaluer**. Si vous souhaitez évaluer la stratégie sélectionnée, il n’y a rien d’autre à faire. Vous pouvez cliquer sur **Afficher** dans la zone **Détails sur les cibles** pour voir les détails des résultats d’évaluation.  
  
3.  Pour afficher toutes les stratégies système des groupes de disponibilité, dans le volet **Sélectionner une page**, cliquez sur **Sélection de la stratégie**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [The Always On health model, part 2: Extending the health model](https://docs.microsoft.com/archive/blogs/sqlalwayson/the-alwayson-health-model-part-2-extending-the-health-model).   
  
  
