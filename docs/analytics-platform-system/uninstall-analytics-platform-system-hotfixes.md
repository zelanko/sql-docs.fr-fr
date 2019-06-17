---
title: Désinstallation de correctifs de système de plateforme d’Analytique dans | Microsoft Docs
description: Désinstallation des correctifs de système de plateforme d’Analytique.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5507eae7bb2f8a5ce138223a031ac4946d9f0030
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62675676"
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Désinstaller des correctifs logiciels Analytique Platform System 
Les étapes suivantes décrivent comment désinstaller un correctif Analytique Platform System précédemment installé.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Prérequis  
Pour effectuer ces étapes, vous devez :  
  
-   Une connexion de système de plateforme d’Analytique avec des autorisations pour accéder à la Console d’administration pour surveiller l’appliance.  
  
-   Le compte d’administrateur de domaine à se connecter à la <em>< appliance_domain ></em> **-HST01** nœud.  
  
-   Le numéro d’article pour le correctif logiciel à désinstaller.  
  
## <a name="HowToUninstallPDW"></a>Pour désinstaller un correctif SQL Server PDW  
  
1.  Ouvrez une session sur le <em>< appliance_domain ></em> **-HST01** nœud en tant que l’administrateur de domaine Fabric.  
  
2.  Utilisez l’exécution en tant qu’option de l’administrateur pour ouvrir une invite de commandes.  
  
3.  Remplacez les répertoires par `C:\PDWINST\Patches\<kbarticle>\media` où *<kbarticle>* est le numéro d’article de Base de connaissances pour le correctif logiciel à désinstaller.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Pour supprimer le correctif logiciel, exécutez la commande suivante.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>Voir aussi  
[Téléchargez et appliquez les mises à jour Microsoft &#40;Analytique Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Désinstaller les mises à jour Microsoft &#40;Analytique Platform System&#41;](uninstall-microsoft-updates.md)  
[Appliquer des correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Maintenance logicielle &#40;Analytique Platform System&#41;](software-servicing.md)  
  
