---
title: Se connecter à un utilitaire SQL Server
description: Découvrez comment vous connecter à un Utilitaire SQL Server afin de pouvoir gérer le contrôle d’intégrité de SQL Server. Vous pouvez vous connecter via SQL Server Management Studio (SSMS).
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fb961ccd1a1ec3013e186c7b45a54004ff400e07
ms.sourcegitcommit: e08d28530e0ee93c78a4eaaee8800fd687babfcc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301788"
---
# <a name="connect-to-a-sql-server-utility"></a>Se connecter à un utilitaire SQL Server

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Avant de vous connecter à un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous devez créer un point de contrôle de l’utilitaire (UCP). Pour plus d’informations, consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md).  

Pour afficher et gérer l’intégrité des ressources de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) pour vous connecter à un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  

Pour vous connecter à un utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] via SSMS :  

1. Lancez SSMS.

2. Dans SSMS, connectez-vous à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

3. Sélectionnez **Afficher**, puis **Explorateur de l’utilitaire**.

4. Dans le volet de navigation de l’Explorateur de l’utilitaire, sélectionnez :::image type="icon" source="media/connect-to-utility.gif" border="false"::: **Se connecter à l’utilitaire**.

5. Dans la boîte de dialogue **Se connecter au serveur** , spécifiez le nom de l’instance de l’UCP, puis sélectionnez **Se connecter**.

6. Affichez le volet Navigation de l’Explorateur de l’utilitaire pour consulter une arborescence des ressources de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans l’UCP.

La création d’un UCP vous connecte également à l’utilitaire [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Créer un point de contrôle de l’utilitaire SQL Server &#40;utilitaire SQL Server&#41;](../../relational-databases/manage/create-a-sql-server-utility-control-point-sql-server-utility.md)

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités et tâches de l’utilitaire SQL Server](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)
- [Consulter les résultats d’une stratégie de contrôle d’intégrité des ressources &#40;utilitaire SQL Server&#41;](../../relational-databases/manage/view-resource-health-policy-results-sql-server-utility.md)