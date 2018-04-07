---
title: Lancez le Gestionnaire de Configuration (système de plateforme Analytique)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b914ba9a-e4ec-4750-934a-c447fc8909e3
caps.latest.revision: 22
ms.openlocfilehash: 0ea02f539633233b462cc6c4cc3cc7ba5d452da9
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="launch-the-configuration-manager"></a>Lancez le Gestionnaire de Configuration
Cette rubrique fournit des instructions pour lancer le **Configuration Manager** pour le matériel de système de plateforme Analytique.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Configuration requise  
Le système de plateforme Analytique**Configuration Manager** peut uniquement être exécutée par l’administrateur de domaine d’application. Pour exécuter cet outil, vous devez le mot de passe pour l’administrateur de domaine d’application. Pour créer d’autres administrateurs de points d’accès, consultez [créer un administrateur de domaine APS &#40;APS&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="Accessing"></a>Lancer l’outil de Configuration Manager  
Pour exécuter le Gestionnaire de Configuration, utilisez Bureau à distance pour se connecter au nœud de contrôle de PDW (***PDW_region *-CTL01**) nœud et vous connecter en tant que * appliance_domain ***\Administrator**. Lors du démarrage de la **Configuration Manager** de programme, utilisez la **exécuter en tant qu’administrateur** option pour vous assurer que vos informations d’identification d’administrateur sont utilisées.  
  
#### <a name="to-launch-from-a-browser-window"></a>Lancement à partir d’une fenêtre de navigateur  
  
1.  Ouvrez un navigateur et accédez au répertoire `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
2.  Avec le bouton droit `dwconfig.exe` puis cliquez sur **exécuter en tant qu’administrateur**.  
  
#### <a name="to-launch-from-a-command-prompt"></a>Lancement à partir d’une invite de commandes  
  
1.  Sur le bureau, ouvrez le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Accessoires**, avec le bouton droit **invite de commandes** puis cliquez sur  **Exécuter en tant qu’administrateur**.  
  
2.  À l’invite de commandes, entrez la commande suivante pour changer de répertoire : `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"`.  
  
3.  À l’invite de commandes, entrez `dwconfig.exe`.  
  
Après le **Configuration Manager** est démarré, vous verrez toutes les fonctionnalités disponibles répertoriées dans le volet gauche. Le reste de cette section explique comment effectuer chaque action disponible dans l’outil.  
  
Pour fermer et quitter **Configuration Manager**, cliquez sur **quitter** dans le coin inférieur droit de n’importe quel écran.  
  
![SQL_Server_PDW_DWConfig_ApplTop](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>Voir aussi  
[Contrôler le matériel à l’aide de la Console d’administration &#40;Analytique plate-forme système&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
