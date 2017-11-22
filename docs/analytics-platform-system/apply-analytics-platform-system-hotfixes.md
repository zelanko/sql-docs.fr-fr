---
title: "Appliquer des correctifs de système de plateforme Analytique (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fca5eec9-86b8-4d20-b498-1678c367b5c8
caps.latest.revision: "25"
ms.openlocfilehash: af879486885f2c27ad4c3d80ef9a3d41279ff0ee
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="apply-analytics-platform-system-hotfixes"></a>Appliquer des correctifs de système de plateforme Analytique
Cette rubrique explique comment appliquer des correctifs pour le logiciel de système de plateforme Analytique.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
> [!WARNING]  
> N’essayez pas d’appliquer un correctif de système de plateforme Analytique si votre matériel ou n’importe quel composant matériel est arrêté ou dans un échec sur l’état. Dans ce cas, contactez le support technique pour assistance.  
  
> [!WARNING]  
> Ne pas appliquer un correctif de système de plateforme Analytique alors que l’application en cours d’utilisation. Application d’un correctif peut entraîner des nœuds de dispositifs de redémarrer. Le correctif logiciel doit être appliqué pendant une fenêtre de maintenance lorsque l’application n’est pas utilisée.  
  
### <a name="prerequisites"></a>Conditions préalables  
Pour effectuer ces étapes, vous devez :  
  
-   Une connexion de système de plateforme Analytique avec des autorisations pour accéder à la Console d’administration pour surveiller l’état de l’application. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   Base de connaissances du compte d’administrateur de domaine de l’ensemble fibre optique pour se connecter à la *< nom_domaine >***-HST01** nœud.  
  
## <a name="HowToInstallPDW"></a>Pour appliquer un correctif de système de plateforme Analytique  
Contrairement aux mises à jour Microsoft, les correctifs pour le logiciel de système de plateforme Analytique ne sont pas gérées via WSUS. Ils ont un flux de travail différent et sont installés par l’exécution d’un package de correctif logiciel.  
  
1.  **Vérifiez les indicateurs d’état appliance.**  
  
    1.  Ouvrez la Console d’administration et accédez à la page État de l’application. Pour plus d’informations, consultez [contrôler le matériel à l’aide de la Console d’administration &#40; Système de plateforme Analytique &#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
    2.  Tous les indicateurs de rouges ou jaunes doivent être résolus avant de passer à l’étape suivante. Deux exceptions à cela sont :  
  
        -   S’il existe des défaillances de disque, utilisez la page des alertes de la Console Administrateur pour vérifier pas plus d’une défaillance de disque au sein de chaque serveur ou une baie de stockage SAN. Cas de défaillance de ne plus d’un disque au sein de chaque serveur ou une baie de stockage SAN, vous pouvez passer à l’étape suivante avant de corriger les erreurs de disque. Veillez à contacter le support Microsoft pour résoudre les échecs de disque dès que possible.  
  
        -   S’il existe une erreur de volume de disque (jaune) non critiques qui n’est pas sur le lecteur C:\, vous pouvez passer à l’étape suivante avant de résoudre l’erreur de volume de disque.  
  
2.  **Installez le correctif logiciel de système de plateforme Analytique**  
  
    1.  Connexion à la <*appliance_domain*>-nœud HST01 comme administrateur de domaine.  
  
    2.  Utilisez le **exécuter en tant qu’administrateur** option pour ouvrir une invite de commandes.  
  
    3.  Exécutez la commande suivante, en remplaçant  *<HotfixPackageName>*  avec le nom de l’exécutable correctif et en remplaçant les autres éléments de l’espace réservé *< >* avec les informations appropriées.  
  
        ```  
        <HotfixPackageName> /DomainAdminPassword="<password>"  
        ```  
  
    4.  Suivez les étapes présentées par le package de correctif logiciel.  
  
## <a name="see-also"></a>Voir aussi  
[Téléchargez et appliquez les mises à jour Microsoft &#40; Système de plateforme Analytique &#41;](download-and-apply-microsoft-updates.md)  
[Désinstaller les mises à jour Microsoft &#40; Système de plateforme Analytique &#41;](uninstall-microsoft-updates.md)  
[Désinstallation des correctifs de système de plateforme Analytique &#40; Système de plateforme Analytique &#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Logiciel de maintenance &#40; Système de plateforme Analytique &#41;](software-servicing.md)  
  
