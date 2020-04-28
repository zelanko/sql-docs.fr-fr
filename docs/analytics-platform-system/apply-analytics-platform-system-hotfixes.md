---
title: Appliquer des correctifs logiciels Analytics Platform System
description: Cet article explique comment appliquer des correctifs au logiciel système de la plateforme d’analyse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: fd62413ec8542aba9f3973d0e8483cb9c5c9128a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401375"
---
# <a name="apply-analytics-platform-system-hotfixes"></a>Appliquer des correctifs logiciels Analytics Platform System
Cet article explique comment appliquer des correctifs au logiciel système de la plateforme d’analyse.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
> [!WARNING]  
> N’essayez pas d’appliquer un correctif logiciel de plateforme d’analyse si votre appliance ou un composant de l’appareil est en panne ou dans un État basculé. Dans ce cas, contactez le support technique pour obtenir de l’aide.  
  
> [!WARNING]  
> N’appliquez pas de correctif logiciel de plateforme d’analyse lorsque l’appareil est en cours d’utilisation. L’application d’un correctif peut entraîner le redémarrage des nœuds de l’appliance. Le correctif doit être appliqué au cours d’une fenêtre de maintenance lorsque l’appareil n’est pas utilisé.  
  
### <a name="prerequisites"></a>Prérequis  
Pour effectuer ces étapes, vous aurez besoin des éléments suivants :  
  
-   Une connexion Analytics Platform System avec des autorisations pour accéder à la console d’administration afin de surveiller l’état de l’appliance. <!-- MISSING LINKS See [Grant Permissions to Use the Admin Console &#40;SQL Server PDW&#41;](../sqlpdw/grant-permissions-to-use-the-admin-console-sql-server-pdw.md).  -->  
  
-   Connaissance du compte d’administrateur de domaine de l’infrastructure pour se connecter au nœud _<domain_name>_ **-HST01** .  
  
## <a name="to-apply-a-analytics-platform-system-hotfix"></a><a name="HowToInstallPDW"></a>Pour appliquer un correctif logiciel de plateforme d’analyse  
Contrairement aux mises à jour Microsoft, les correctifs logiciels pour le logiciel système de la plateforme d’analyse ne sont pas gérés par le biais de WSUS. Ils disposent d’un flux de travail différent et sont installés en exécutant un package de correctifs.  
  
1.  **Vérifiez les indicateurs d’état de l’appliance.**  
  
    1.  Ouvrez la console d’administration et accédez à la page État de l’appliance. Pour plus d’informations, consultez [surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
    2.  Tous les indicateurs rouges ou jaunes doivent être résolus avant de passer à l’étape suivante. Voici quelques exceptions :  
  
        -   En cas de défaillances de disque, utilisez la page alertes de la console d’administration pour vérifier qu’il n’y a pas plus d’une défaillance de disque au sein de chaque serveur ou groupe SAN. S’il n’y a pas plus d’une défaillance de disque au sein de chaque serveur ou groupe SAN, vous pouvez passer à l’étape suivante avant de résoudre les défaillances de disque. Veillez à contacter le support Microsoft pour résoudre les défaillances de disque dès que possible.  
  
        -   S’il y a une erreur de volume de disque non critique (jaune) qui ne se trouve pas sur le lecteur C:\ , vous pouvez passer à l’étape suivante avant de résoudre l’erreur de volume de disque.  
  
2.  **Installer le correctif logiciel Analytics Platform System**  
  
    1.  Connectez-vous au nœud <*appliance_domain*>-HST01 en tant qu’administrateur de domaine.  
  
    2.  Utilisez l’option **exécuter en tant qu’administrateur** pour ouvrir une invite de commandes.  
  
    3.  Exécutez la commande suivante, en *<HotfixPackageName>* remplaçant par le nom du package exécutable du correctif logiciel, et en remplaçant les autres éléments d’espace réservé *<  >* par les informations appropriées.  
  
        ```  
        <HotfixPackageName> /DomainAdminPassword="<password>"  
        ```  
  
    4.  Suivez les étapes fournies par le package de correctifs.  
  
## <a name="see-also"></a>Voir aussi  
[Téléchargez et appliquez les mises à jour Microsoft &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Désinstallez les mises à jour Microsoft &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Désinstallation des correctifs du système de plateforme Analytics &#40;Analytics&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Maintenance logicielle &#40;système de plateforme Analytics&#41;](software-servicing.md)  
  
