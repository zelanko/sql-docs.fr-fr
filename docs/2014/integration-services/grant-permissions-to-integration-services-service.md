---
title: Accorder des autorisations à Integration Services service | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c2caa68-7834-4ea0-bd77-4f3a7c86d634
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 7a71b6b18960ee5b457be339e8a98ada505a6dec
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966249"
---
# <a name="grant-permissions-to-integration-services-service"></a>Accorder des autorisations au service Integration Services
  Dans les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], par défaut, lorsque vous installiez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , tous les utilisateurs du groupe Utilisateurs avaient accès au service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Lorsque vous installez la version actuelle de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], les utilisateurs n'ont pas accès au service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Ce service est sécurisé par défaut. Une fois [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installé, l'administrateur doit accorder l'accès au service.  
  
### <a name="to-grant-access-to-the-integration-services-service"></a>Pour accorder l'accès au service Integration Services  
  
1.  Exécutez Dcomcnfg.exe. Dcomcnfg.exe fournit une interface utilisateur qui permet de modifier certains paramètres du Registre.  
  
2.  Dans la boîte de dialogue **Services de composants**, développez le nœud Services de composants > Ordinateurs > Poste de travail > Configuration DCOM.  
  
3.  Cliquez avec le bouton droit sur **Microsoft SQL Server Integration Services 12,0**, puis cliquez sur **Propriétés**.  
  
4.  Sous l'onglet **Sécurité** , cliquez sur **Modifier** dans la zone **Autorisations d'exécution et d'activation** .  
  
5.  Ajoutez des utilisateurs et affectez les autorisations appropriées, puis cliquez sur OK.  
  
6.  Répétez les étapes 4 à 5 pour les autorisations d'accès.  
  
7.  Redémarrez SQL Server Management Studio.  
  
8.  Redémarrez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
  
