---
title: Consulter les résultats d’une stratégie de contrôle d’intégrité des ressources (utilitaire SQL Server) | Microsoft Docs
description: Découvrez comment utiliser SQL Server Management Studio pour afficher les résultats de la stratégie de contrôle d’intégrité des ressources de l’utilitaire SQL Server pour les instances de SQL Server et les applications de la couche de données.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 80cb14fb-f4c6-4be2-ba17-eb4e4cddd35f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a3ec26ba8988f36e3deac88373a932ef377f8d59
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810026"
---
# <a name="view-resource-health-policy-results-sql-server-utility"></a>Consulter les résultats d'une stratégie de contrôle d'intégrité des ressources (Utilitaire SQL Server)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Utilisez le tableau de bord de l’utilitaire dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour consulter les paramètres des ressources de l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour les instances managées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les applications de la couche Données. Pour plus d’informations, consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  

##  <a name="SSMSProcedure"></a>

### <a name="view-sql-server-utility-resource-health-policy-results"></a>Consulter les résultats d'une stratégie de contrôle d'intégrité des ressources de l'utilitaire SQL Server.  

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS), sélectionnez **Affichage**, puis **Explorateur de l’utilitaire** pour afficher le volet Navigation de l’Explorateur de l’utilitaire. Pour afficher le volet de contenu, sélectionnez **Affichage**, puis **Contenu de l’Explorateur de l’utilitaire**.  

2. Dans le volet Navigation, sélectionnez ![Se connecter à l’utilitaire](../../relational-databases/manage/media/connect-to-utility.gif "Connect_to_Utility")**Se connecter à l’utilitaire**. Si vous n’avez pas créé de point de contrôle d’utilitaire (UCP) ou si vous n’avez pas inscrit d’instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d’applications de la couche Données dans l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  

3. Sélectionnez le nœud UCP pour afficher les données de synthèse des instances managées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des applications de la couche Données (cliquez avec le bouton droit pour actualiser). Les données du tableau de bord sont affichées dans le volet Contenu.  

4. Sélectionnez le nœud **Instances managées** pour afficher les données en mode Liste des instances managées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (cliquez avec le bouton droit pour actualiser). Les données en mode Liste sont affichées dans le volet Contenu.  

5. Sélectionnez le nœud **Applications de la couche Données déployées** pour afficher les données en mode Liste des applications de la couche Données (cliquez avec le bouton droit pour actualiser). Les données en mode Liste sont affichées dans le volet Contenu.  

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)
- [Réduire le bruit dans les stratégies d’utilisation du processeur &#40;utilitaire SQL Server&#41;](../../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)
- [Détails des applications de la couche Données déployées &#40;Utilitaire SQL Server&#41;](/previous-versions/sql/sql-server-2016/ee240857(v=sql.130))
- [Détails de Managed Instance &#40;Utilitaire SQL Server&#41;](./utility-explorer-f1-help.md)
- [Administration de l’utilitaire &#40;utilitaire SQL Server&#41;](/previous-versions/sql/sql-server-2016/ee240832(v=sql.130))