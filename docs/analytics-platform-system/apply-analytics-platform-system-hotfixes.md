---
title: Appliquer des correctifs logiciels Analytique Platform System | Microsoft Docs
description: Cet article explique comment appliquer des correctifs au logiciel Analytique Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b4b72017bb23ae44da9c5884f0ebf2a8b099fd3e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63019044"
---
# <a name="apply-analytics-platform-system-hotfixes"></a>Appliquer des correctifs logiciels Analytics Platform System
Cet article explique comment appliquer des correctifs au logiciel Analytique Platform System.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
> [!WARNING]  
> N’essayez pas d’appliquer un correctif logiciel Analytique Platform System si votre appliance ou n’importe quel composant de l’appliance est arrêté ou dans un état de pointage. Dans ce cas, contactez le support pour obtenir une assistance.  
  
> [!WARNING]  
> Ne pas appliquer un correctif logiciel Analytique Platform System tandis que l’appliance est en cours d’utilisation. Application d’un correctif peut provoquer des nœuds d’appliance à redémarrer. Le correctif logiciel doit être appliqué pendant une fenêtre de maintenance lors de l’appliance n’est pas utilisée.  
  
### <a name="prerequisites"></a>Prérequis  
Pour effectuer ces étapes, vous devez :  
  
-   Une connexion de système de plateforme d’Analytique avec des autorisations pour accéder à la Console d’administration pour surveiller l’état de l’appliance. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   Base de connaissances du compte d’administrateur de domaine Fabric pour vous connecter à la _< nom_domaine >_**-HST01** nœud.  
  
## <a name="HowToInstallPDW"></a>Pour appliquer un correctif logiciel Analytique Platform System  
Contrairement aux mises à jour Microsoft, les correctifs logiciels pour le logiciel de système de plateforme d’Analytique ne sont pas gérées via WSUS. Ils ont un flux de travail différent et sont installés en exécutant un package de correctif logiciel.  
  
1.  **Vérifiez les indicateurs d’état appliance.**  
  
    1.  Ouvrez la Console d’administration et accédez à la page d’état de l’Appliance. Pour plus d’informations, consultez [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
    2.  Tous les indicateurs rouges ou jaunes doivent être résolues avant de passer à l’étape suivante. Deux exceptions à cela sont :  
  
        -   S’il existe des défaillances de disque, utilisez la page des alertes de la Console Administrateur vérifier que pas plus d’une défaillance de disque au sein de chaque serveur ou de la baie de SAN. En cas de défaillance de disque ne plusieurs au sein de chaque serveur ou de la baie de SAN, vous pouvez passer à l’étape suivante avant de corriger l’échec (s) disque. Veillez à contacter le support Microsoft pour résoudre l’échec (s) disque dès que possible.  
  
        -   S’il existe une erreur de volume de disque (jaune) non critiques qui n’est pas sur le lecteur C:\, vous pouvez passer à l’étape suivante avant de résoudre l’erreur de volume de disque.  
  
2.  **Installez le correctif logiciel Analytique Platform System**  
  
    1.  Connexion à la <*appliance_domain*>-nœud HST01 comme administrateur de domaine.  
  
    2.  Utilisez le **exécuter en tant qu’administrateur** option pour ouvrir une invite de commandes.  
  
    3.  Exécutez la commande suivante, en remplaçant *<HotfixPackageName>* avec le nom du package exécutable correctif et en remplaçant les autres éléments de l’espace réservé *< >* avec les informations appropriées.  
  
        ```  
        <HotfixPackageName> /DomainAdminPassword="<password>"  
        ```  
  
    4.  Suivez les étapes présentées par le package de correctif logiciel.  
  
## <a name="see-also"></a>Voir aussi  
[Téléchargez et appliquez les mises à jour Microsoft &#40;Analytique Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Désinstaller les mises à jour Microsoft &#40;Analytique Platform System&#41;](uninstall-microsoft-updates.md)  
[Désinstallation de correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Maintenance logicielle &#40;Analytique Platform System&#41;](software-servicing.md)  
  
