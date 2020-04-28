---
title: Désinstaller des mises à jour Microsoft
description: Désinstallez les mises à jour Microsoft dans Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: a5ebe1ee911f7500505cdbd1962d28c35461a635
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74399464"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Désinstaller les mises à jour Microsoft dans Analytics Platform System
Cet article explique comment désinstaller une mise à jour Microsoft précédemment installée sur l’appliance Analytics Platform System.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Prérequis  
Pour effectuer ces étapes, vous aurez besoin des éléments suivants :  
  
-   Une connexion Analytics Platform System avec des autorisations pour accéder à la console d’administration afin de surveiller l’appliance.  
  
-   Connaissance du compte d’administrateur de domaine de l’infrastructure pour la <em> <Fabric Domain> </em>connexion au nœud **-HST01** .  
  
## <a name="to-uninstall-microsoft-updates"></a><a name="HowToUninstallMSFT"></a>Pour désinstaller les mises à jour Microsoft  
  
1.  Connectez-vous au <em> <Fabric Domain> </em>nœud **-HST01** en tant qu’administrateur de domaine de l’infrastructure.  
  
2.  Pour désinstaller toutes les mises à jour approuvées pour WSUS, ouvrez une fenêtre d’invite de commandes et entrez la commande suivante. Remplacez les éléments d’espace réservé *<  >* par les informations appropriées.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>Étapes suivantes
Pour plus d'informations, consultez les pages suivantes :
- [Téléchargez et appliquez les mises à jour Microsoft &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) 
- [Appliquer des correctifs logiciels Analytics Platform System &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Désinstallation des correctifs du système de plateforme Analytics &#40;Analytics&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [Maintenance logicielle &#40;système de plateforme Analytics&#41;](software-servicing.md)  
  
