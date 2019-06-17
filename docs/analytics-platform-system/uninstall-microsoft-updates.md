---
title: Désinstaller les mises à jour de Microsoft - Analytique Platform System | Microsoft Docs »
description: Désinstaller les mises à jour de Microsoft dans Analytique Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4739d05b1878c8b7fc9f66f2e0b8145ff1044e54
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63243826"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Désinstaller les mises à jour de Microsoft d’Analytique Platform System
Cet article décrit comment désinstaller une mise à jour de Microsoft précédemment installée sur l’appliance Analytique Platform System.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Prérequis  
Pour effectuer ces étapes, vous devez :  
  
-   Une connexion de système de plateforme d’Analytique avec des autorisations pour accéder à la Console d’administration pour surveiller l’appliance.  
  
-   Base de connaissances du compte d’administrateur de domaine Fabric pour vous connecter à la <em> <Fabric Domain> </em> **-HST01** nœud.  
  
## <a name="HowToUninstallMSFT"></a>Pour désinstaller les mises à jour Microsoft  
  
1.  Connectez-vous à la <em> <Fabric Domain> </em> **-HST01** nœud en tant que l’administrateur de domaine Fabric.  
  
2.  Pour désinstaller toutes les mises à jour qui sont approuvées pour WSUS désinstaller, ouvrez une fenêtre d’invite de commandes et entrez la commande suivante. Remplacez les éléments de l’espace réservé *< >* avec les informations appropriées.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>Étapes suivantes
Pour plus d'informations, consultez :
- [Téléchargez et appliquez les mises à jour Microsoft &#40;Analytique Platform System&#41;](download-and-apply-microsoft-updates.md) 
- [Appliquer des correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Désinstallation de correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [Maintenance logicielle &#40;Analytique Platform System&#41;](software-servicing.md)  
  
