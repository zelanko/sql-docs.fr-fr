---
title: organiser les travaux
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job category
- organize jobs
ms.assetid: 629c3e06-f933-483b-8621-280dbb7a7bd1
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a02f50ed88a2883d0149dbbd37df63b27e87dfa4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75247612"
---
# <a name="organize-jobs"></a>organiser les travaux
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Les catégories de travaux permettent d'organiser les travaux afin d'en faciliter le filtrage et le regroupement. Par exemple, vous pouvez organiser tous vos travaux de sauvegarde de base de données dans la catégorie Maintenance de bases de données. Vous pouvez également créer vos propres catégories de travaux.  
  
> [!WARNING]  
> Les catégories multiserveurs n'existent que sur un serveur maître. Il n’y a qu’une seule catégorie de travaux par défaut disponible sur un serveur maître : [**N’appartenant à aucune catégorie (Multiserveurs)** ]. Lors du téléchargement d'un travail multiserveur, sa catégorie passe à **Travaux de MSX** sur le serveur cible.  
  
## <a name="related-tasks"></a>Tâches associées  
  
|||  
|-|-|  
|**Description**|**Rubrique**|  
|Explique comment créer une catégorie de travaux.|[Créer une catégorie de travaux](../../ssms/agent/create-a-job-category.md)|  
|Explique comment supprimer une catégorie de travaux.|[Supprimer une catégorie de travaux](../../ssms/agent/delete-a-job-category.md)|  
|Explique comment attribuer un travail à une catégorie de travaux.|[Affecter un travail à une catégorie de travaux](../../ssms/agent/assign-a-job-to-a-job-category.md)|  
|Décrit comment modifier l'appartenance à une catégorie de travaux.|[Modifier l’appartenance d’une catégorie de travaux](../../ssms/agent/change-the-membership-of-a-job-category.md)|  
|Décrit comment répertorier les informations de catégorie.|[Répertorier les informations de catégorie de travaux](../../ssms/agent/list-job-category-information.md)|  
  
