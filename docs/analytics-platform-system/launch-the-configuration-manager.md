---
title: Lancez le Gestionnaire de Configuration - Analytique Platform System | Microsoft Docs
description: Instructions pour lancer l’outil de Configuration Manager pour l’appliance Analytique Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7aef9ada4a93605460cf2759dbe9deeddfc9e0d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960725"
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Lancez le Gestionnaire de Configuration d’Analytique Platform System
Cette rubrique fournit des instructions pour lancer le **Configuration Manager** pour l’appliance Analytique Platform System.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Prérequis  
Le système de plateforme Analytique**Configuration Manager** peut uniquement être exécuté par l’administrateur de domaine d’appliance. Pour exécuter cet outil, vous devez le mot de passe pour l’administrateur de domaine d’application. Pour créer des administrateurs de points d’accès supplémentaires, consultez [créer un administrateur de domaine APS &#40;APS&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="Accessing"></a>Lancez l’outil de Configuration Manager  
Pour exécuter le Gestionnaire de Configuration, utilisez Bureau à distance pour se connecter au nœud de contrôle de PDW ( **_PDW_region_-CTL01**) nœud et connectez-vous en tant que _appliance_domain_ **\Administrator**. Lors du démarrage de la **Configuration Manager** du programme, utilisez la **exécuter en tant qu’administrateur** option pour vous assurer que vos informations d’identification administrateur sont utilisées.  
  
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
[Surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
