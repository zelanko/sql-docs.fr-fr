---
title: Comptes de domaine requis pour la batterie de serveurs SharePoint (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 90cd6d3e-a271-4cb8-81f2-fc555b2d3cab
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c4079ea4213d7ecbec0165c32c82b3449bbb5aee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952510"
---
# <a name="domain-accounts-required-for-sharepoint-farm-upgrade-advisor"></a>Comptes de domaine requis pour la batterie de serveurs SharePoint (Conseiller de mise à niveau)
  Les produits SharePoint configurés pour un environnement de batterie requièrent l'utilisation de comptes de domaine.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRS](../../includes/ssrs.md)]  
  
### <a name="description"></a>Description  
 Les produits SharePoint configurés pour un environnement de batterie requièrent l'utilisation de comptes de domaine pour les services et les connexions de base de données. Cette exigence concerne notamment le compte spécifié pour le compte de service Reporting Services.  
  
 Si vous n'utilisez pas de compte d'utilisateur de domaine pour Reporting Services, vous rencontrez des problèmes notamment en consultant les pages Administration centrale de SharePoint 2010. Lorsque vous essayez de configurer l'intégration de Reporting Services, un message d'erreur semblable au suivant s'affiche :  
  
 « Le serveur de rapports s'exécute sous le compte NT AUTHORITY\NETWORK SERVICE intégré, qui n'est pas pris en charge par les batteries de serveurs SharePoint. Reconfigurez le serveur de rapports pour qu’il s’exécute sous un compte de domaine.»  
  
## <a name="corrective-action"></a>Action corrective  
 Pour [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les versions précédentes, utilisez la gestionnaire de configuration de Reporting Services pour modifier le compte qui est affecté en tant que compte de service Report Server.  
  
#### <a name="to-change-the-service-account-from-configuration-manager"></a>Pour modifier le compte de service à partir du Gestionnaire de configuration  
  
1.  Dans le menu **Démarrer** , sélectionnez **tous les programmes**, puis cliquez sur **Microsoft SQL Server 2008 R2**.  
  
2.  Sélectionnez **outils de configuration**, puis cliquez sur **Gestionnaire de configuration de Reporting Services**.  
  
3.  Dans Configuration Manager, sélectionnez l’onglet **compte de service** .  
  
4.  Sélectionnez **utiliser un autre compte** et entrez les informations d’identification d’un compte de domaine.  
  
5.  Cliquez sur **Appliquer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)  
  
  
