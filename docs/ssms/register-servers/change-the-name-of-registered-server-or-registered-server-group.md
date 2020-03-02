---
title: Changer le nom d’un serveur ou d’un groupe de serveurs inscrits
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/02/2016
ms.openlocfilehash: cefef29e85ea4494faaa10385c45fc45a77a7e1e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "75258893"
---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>Changer le nom d’un serveur ou d’un groupe de serveurs inscrits

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Cette rubrique explique comment modifier le nom d'un serveur ou d'un groupe de serveurs dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Ce nom peut être modifié à tout moment. La modification du nom d'un serveur inscrit porte uniquement sur la manière dont le nom est affiché. Pour vous connecter à un autre serveur, vous devez modifier les propriétés de connexion du serveur inscrit.  
  
## <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio

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