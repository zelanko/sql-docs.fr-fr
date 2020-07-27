---
title: Afficher le journal des applications Windows (Windows) | Microsoft Docs
description: Quand SQL Server est configuré pour vous permettre d’utiliser le journal des applications Windows, chaque session y enregistre des événements. Découvrez comment afficher le journal des applications Windows.
ms.custom: ''
ms.date: 02/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- viewing logs
- application logs [SQL Server]
- logs [SQL Server], application
- monitoring Windows NT application log [SQL Server]
- Windows NT application logs [SQL Server]
- displaying logs
- monitoring [SQL Server], events
- logs [SQL Server], viewing
ms.assetid: 168a6c6e-12df-46a9-9904-55d63ca8fe14
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: d733c8c50768f5639c1af8b20f9c2b9028f7cfc1
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458681"
---
# <a name="view-the-windows-application-log-windows-10"></a>Afficher le journal des applications Windows (Windows 10)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour vous permettre d’utiliser le journal des applications Windows, chaque session [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y enregistre de nouveaux événements. Contrairement au journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un nouveau journal des applications n'est pas créé chaque fois que vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="view-the-windows-application-log"></a>Consulter le journal des applications Windows  
  
1. Dans la **barre de recherche**, tapez **Observateur d’événements**, puis sélectionnez l’application de bureau **Observateur d’événements**.
  
2. Dans **l’Observateur d’événements**, ouvrez **Journaux des applications et des services**.

3. Les événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont identifiés par l’entrée **MSSQLSERVER** (les instances nommées sont identifiées par **MSSQL$** _<nom_instance>_ ) dans la colonne **Source**. Les événements de SQL Server Agent sont identifiés par l’entrée SQLSERVERAGENT (pour les instances nommées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les événements de l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont identifiés par **SQLAgent$** \<*instance_name*>). Les événements du service Microsoft Search sont identifiés par l'entrée **Microsoft Search**.  
  
4. Pour afficher le journal d’un autre ordinateur, cliquez avec le bouton droit sur **Observateur d’événements (local)** . Sélectionnez **Se connecter à un autre ordinateur**, puis renseignez les champs de la boîte de dialogue **Sélectionner un ordinateur**.  
  
5. Si vous le souhaitez, pour afficher uniquement les événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dans le menu **Afficher**, sélectionnez **Filtrer**. Dans la liste **Source de l’événement**, sélectionnez **MSSQLSERVER**. Pour afficher uniquement les événements de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez **SQLSERVERAGENT** dans la liste **Source de l'événement** .  
  
6. Pour obtenir plus de détails sur un événement particulier, double-cliquez sur cet événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher le journal des erreurs SQL Server &#40;SQL Server Management Studio&#41;](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md)  
  
  
