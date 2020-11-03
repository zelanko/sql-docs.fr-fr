---
title: Lancer Configuration Manager
description: Instructions de lancement de l’outil Configuration Manager pour l’appliance Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: be69331ec9f9daa091035d6ef21142c4f40d6a84
ms.sourcegitcommit: 442fbe1655d629ecef273b02fae1beb2455a762e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93235166"
---
# <a name="launch-the-configuration-manager-in-analytics-platform-system"></a>Lancer le Configuration Manager dans Analytics Platform System
Cette rubrique fournit des instructions sur le lancement de la **Configuration Manager** pour l’appliance Analytics Platform System.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Prérequis  
Le système Analytics Platform System **Configuration Manager** ne peut être exécuté que par l’administrateur du domaine de l’appliance. Pour exécuter cet outil, vous avez besoin du mot de passe de l’administrateur de domaine de l’appliance. Pour créer des administrateurs APS supplémentaires, voir [créer un administrateur de domaine aps &#40;aps&#41;](create-an-aps-domain-administrator-aps.md).  
  
## <a name="launch-the-configuration-manager-tool"></a><a name="Accessing"></a>Lancer l’outil Configuration Manager  
Pour exécuter le Configuration Manager, utilisez Bureau à distance pour vous connecter au nœud de contrôle PDW ( **_PDW_region_ -CTL01** ) et connectez-vous en tant que _appliance_domain_**\Administrateur** . Lors du démarrage du programme **Configuration Manager** , utilisez l’option **exécuter en tant qu’administrateur** pour vous assurer que vos informations d’identification d’administrateur sont utilisées.  
  
#### <a name="to-launch-from-a-browser-window"></a>Pour lancer à partir d’une fenêtre de navigateur  
  
1.  Ouvrez un navigateur et accédez au répertoire `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100` .  
  
2.  Cliquez avec le bouton droit sur `dwconfig.exe` , puis cliquez sur **exécuter en tant qu’administrateur** .  
  
#### <a name="to-launch-from-a-command-prompt"></a>Pour lancer à partir d’une invite de commandes  
  
1.  Sur le bureau, ouvrez le menu **Démarrer** , cliquez sur **programmes** , **accessoires** , cliquez avec le bouton droit sur **invite de commandes** , puis cliquez sur **exécuter en tant qu’administrateur** .  
  
2.  À l’invite de commandes, entrez la commande suivante pour modifier les répertoires : `cd /d "C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100"` .  
  
3.  À l'invite de commandes, entrez `dwconfig.exe`.  
  
Une fois le **Configuration Manager** démarré, toutes les fonctionnalités disponibles sont affichées dans le volet gauche. Le reste de cette section explique comment effectuer chaque action disponible dans l’outil.  
  
Pour fermer et quitter **Configuration Manager** , cliquez sur **quitter** dans le coin inférieur droit de n’importe quel écran.  
  
![Capture d’écran de la boîte de dialogue Microsoft Analytics Platform System Configuration Manager montrant la topologie de l’appliance.](./media/launch-the-configuration-manager/SQL_Server_PDW_DWConfig_ApplTop.png "SQL_Server_PDW_DWConfig_ApplTop")  
  
## <a name="see-also"></a>Voir aussi  
[Surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
