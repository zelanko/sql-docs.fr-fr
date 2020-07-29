---
title: Changer le nom d’un serveur ou d’un groupe de serveurs inscrits
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/02/2016
ms.openlocfilehash: 32f59e2db98280a7d096e0f1f7d1a90895db010b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001784"
---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>Changer le nom d’un serveur ou d’un groupe de serveurs inscrits

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Cette rubrique explique comment modifier le nom d'un serveur ou d'un groupe de serveurs dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Ce nom peut être modifié à tout moment. La modification du nom d'un serveur inscrit porte uniquement sur la manière dont le nom est affiché. Pour vous connecter à un autre serveur, vous devez modifier les propriétés de connexion du serveur inscrit.  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio

Dans le menu, accédez à **Afficher\\les serveurs inscrits** afin d’ouvrir le volet **Serveurs inscrits**.

### <a name="to-change-the-name-of-a-server"></a>Pour modifier le nom d'un serveur

1. Dans **Serveurs inscrits**, développez **Moteur de base de données** , puis **Groupes de serveurs locaux**.  

2. Cliquez avec le bouton droit sur le serveur, puis sélectionnez **Propriétés** pour ouvrir la boîte de dialogue **Modifier les propriétés d’inscription du serveur** .

3. Dans la zone **Nom du serveur inscrit** , tapez le nouveau nom pour l’inscription du serveur, puis cliquez sur **Enregistrer**.  

### <a name="to-change-the-name-of-a-server-group"></a>Pour modifier le nom d'un groupe de serveurs  

1. Dans **Serveurs inscrits**, développez **Moteur de base de données** , puis **Groupes de serveurs locaux**.  

2. Cliquez avec le bouton droit sur le groupe de serveurs, puis sélectionnez **Propriétés** pour ouvrir la boîte de dialogue **Modifier les propriétés du groupe de serveurs** . 

3. Dans la zone **Nom de groupe** , tapez le nouveau nom du groupe de serveurs, puis cliquez sur **Enregistrer**.  

## <a name="see-also"></a>Voir aussi

[Modifier l’inscription d’un serveur &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/change-a-server-s-registration-sql-server-management-studio.md)