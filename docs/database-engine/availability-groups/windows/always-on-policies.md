---
title: Évaluer l’intégrité du groupe de disponibilité à l’aide de stratégies de groupe
description: Découvrez comment afficher les stratégies système des groupes de disponibilité qui sont utilisées par le tableau de bord Always On pour fournir des informations sur l’intégrité d’un groupe de disponibilité.
ms.custom: ag-guide, seodec18
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 26bf8f71-c2b8-45ef-b3a3-372b96c9e6e3
author: rothja
ms.author: jroth
manager: jroth
ms.openlocfilehash: 2f8fb49b90a0da28a4961806c7ace46bcb10f5db
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66789452"
---
# <a name="evaluate-health-of-the-always-on-availability-group-using-group-policies"></a>Évaluer l’intégrité du groupe de disponibilité Always On à l’aide de stratégies de groupe
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les stratégies système des groupes de disponibilité Always On sont utilisées par le tableau de bord Always On pour fournir des informations sur l’intégrité d’un groupe de disponibilité à l’utilisateur. Elles sont très utiles pour la résolution initiale des problèmes opérationnels affectant un groupe de disponibilité. Vous pouvez étendre ces stratégies et les utiliser pour personnaliser le tableau de bord Always On ou les exécuter instantanément pour générer les informations d’intégrité désirées.  
  
 Il existe 14 stratégies système pour les groupes de disponibilité. Pour plus d’informations sur chaque stratégie, consultez [Stratégies Always On pour les problèmes opérationnels avec des groupes de disponibilité Always On (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).  
  
## <a name="view-or-evaluate-availability-groups-system-policies"></a>Afficher ou évaluer les stratégies système des groupes de disponibilité  
 Pour afficher ou exécuter les stratégies système des groupes de disponibilité dans SSMS (SQL Server Management Studio), effectuez les étapes suivantes :  
  
1.  Dans **l’Explorateur d’objets**, développez **Gestion**, **Gestion de la stratégie**, **Stratégies**, puis **Stratégies système**.  
  
2.  Cliquez avec le bouton droit sur l’une des stratégies, puis cliquez sur **Évaluer**. Si vous souhaitez évaluer la stratégie sélectionnée, il n’y a rien d’autre à faire. Vous pouvez cliquer sur **Afficher** dans la zone **Détails sur les cibles** pour voir les détails des résultats d’évaluation.  
  
3.  Pour afficher toutes les stratégies système des groupes de disponibilité, dans le volet **Sélectionner une page**, cliquez sur **Sélection de la stratégie**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [The Always On health model, part 2: Extending the health model](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx) (Modèle d’intégrité Always On Partie 2 : Extension du modèle d’intégrité).   
  
  
