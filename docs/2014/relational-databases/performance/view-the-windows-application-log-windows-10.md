---
title: Afficher le journal des applications Windows (Windows) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b18643f97a328dfee94bc5bfe125d6eddeae4efe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150441"
---
# <a name="view-the-windows-application-log-windows"></a>Afficher le journal des applications Windows (Windows)
  Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour vous permettre d'utiliser le journal des applications Windows, chaque session [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] y enregistre des nouveaux événements. Contrairement au journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un nouveau journal des applications n'est pas créé chaque fois que vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="to-view-the-windows-application-log"></a>Pour consulter le journal des applications Windows  
  
1.  Dans le menu **Démarrer** , pointez successivement sur **Tous les programmes**et **Outils d'administration**, puis cliquez sur **Observateur d’événements**.  
  
2.  Dans l'Observateur d'événements, cliquez sur **Application**.  
  
3.  Les événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont identifiés par l’entrée **MSSQLSERVER** (les instances nommées sont identifiées par **MSSQL$** _<nom_instance>_ ) dans la colonne **Source**. Les événements de SQL Server Agent sont identifiés par l’entrée SQLSERVERAGENT (pour les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nommées, les événements de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sont identifiés par **SQLAgent$** \<*nom_instance*>). Les événements du service Microsoft Search sont identifiés par l'entrée **Microsoft Search**.  
  
4.  Pour afficher le journal d’un autre ordinateur, cliquez avec le bouton droit sur **Observateur d’événements**, cliquez sur **Se connecter à un autre ordinateur**, et renseignez la boîte de dialogue **Sélectionner un ordinateur**.  
  
5.  Pour afficher uniquement les événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , dans le menu **Affichage** , cliquez sur **Filtrer**et dans la liste **Source de l'événement** , sélectionnez **MSSQLSERVER**. Pour afficher uniquement les événements de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez **SQLSERVERAGENT** dans la liste **Source de l'événement** .  
  
6.  Pour obtenir plus de détails sur un événement particulier, double-cliquez sur cet événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichez le journal des erreurs SQL Server &#40;SQL Server Management Studio&#41;](../../ssms/sql-server-management-studio-ssms.md)  
  
  
