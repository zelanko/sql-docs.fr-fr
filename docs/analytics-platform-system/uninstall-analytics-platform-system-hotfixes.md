---
title: Désinstaller les correctifs
description: Désinstallez les correctifs logiciels Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ef6929aeb06c9472eb3ff210de016117a9636ded
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "74399763"
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Désinstaller les correctifs logiciels d’Analytics Platform System 
Les étapes suivantes décrivent comment désinstaller un correctif logiciel d’Analytics Platform System précédemment installé.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="prerequisites"></a>Prérequis  
Pour effectuer ces étapes, vous aurez besoin des éléments suivants :  
  
-   Une connexion Analytics Platform System avec des autorisations pour accéder à la console d’administration afin de surveiller l’appliance.  
  
-   Compte d’administrateur de domaine pour se connecter au nœud <em><appliance_domain></em> **-HST01** .  
  
-   Numéro d’article de la base de connaissances pour le correctif logiciel à désinstaller.  
  
## <a name="to-uninstall-a-sql-server-pdw-hotfix"></a><a name="HowToUninstallPDW"></a>Pour désinstaller un correctif logiciel SQL Server PDW  
  
1.  Connectez-vous au nœud <em><appliance_domain></em> **-HST01** en tant qu’administrateur de domaine de l’infrastructure.  
  
2.  Utilisez l’option Exécuter en tant qu’administrateur pour ouvrir une invite de commandes.  
  
3.  Accédez au répertoire `C:\PDWINST\Patches\<kbarticle>\media` où *<kbarticle>* se trouve le numéro d’article de la base de connaissances pour le correctif à désinstaller.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Pour supprimer le correctif, exécutez la commande suivante.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>Voir aussi  
[Téléchargez et appliquez les mises à jour Microsoft &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Désinstallez les mises à jour Microsoft &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Appliquer des correctifs logiciels Analytics Platform System &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Maintenance logicielle &#40;système de plateforme Analytics&#41;](software-servicing.md)  
  
