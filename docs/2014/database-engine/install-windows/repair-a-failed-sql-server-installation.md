---
title: Supprimer une Installation SQL Server 2014 | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 90c11b28-892b-44d6-978e-0eee48c75b7d
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e166059c1ea7e93672dc752bef0de5508f20a46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045015"
---
# <a name="drop-a-sql-server-2014-installation"></a>Ignorer une installation de SQL Server 2014
  L'opération de réparation peut être utilisée dans les scénarios suivants :  
  
-   Réparer une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est endommagée après une installation réussie.  
  
-   Réparer une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si l'opération de mise à niveau est annulée ou échoue une fois que le nom de l'instance est mappé à l'instance nouvellement mise à niveau.  
  
    -   Si le message suivant s'affiche dans le journal résumé, vous pouvez réparer l'instance de mise à niveau qui a échoué :  
  
         La mise à niveau de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a échoué. Pour continuer, déterminez la cause de l'échec, résolvez le problème, puis réparez votre installation. »  
  
    -   Si le message suivant s'affiche dans le journal résumé, vous devez désinstaller, puis réinstaller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous ne pouvez pas réparer l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
         La mise à niveau de[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a échoué. Pour continuer, déterminez la cause de l'échec, résolvez le problème. »  
  
 Lorsque vous réparez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   tous les fichiers manquants ou endommagés sont remplacés ;  
  
-   toutes les clés de Registre manquantes ou endommagées sont remplacées ;  
  
-   les valeurs par défaut sont définies pour toutes les valeurs de configuration manquantes ou non valides.  
  
 Avant de continuer, pour les clusters de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , passez en revue les informations importantes suivantes :  
  
-   La réparation doit être effectuée sur des nœuds de cluster individuels.  
  
-   Pour réparer un nœud de cluster de basculement après une préparation ayant échoué, utilisez **Supprimer un nœud** et effectuez à nouveau la préparation. Pour plus d’informations, consultez [Ajouter ou supprimer des nœuds dans un cluster de basculement SQL Server &#40;programme d’installation&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
### <a name="to-repair-a-failed-installation-of-includessnoversionincludesssnoversion-mdmd-from-the-installation-center"></a>Pour réparer une installation défectueuse de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir du centre d'installation  
  
1.  Lancez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (setup.exe) à partir du support d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
2.  Après avoir vérifié les composants requis et le système, le programme d'installation affiche la page Centre d'installation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
3.  Cliquez sur **Maintenance** dans la zone de navigation gauche, puis sur **Réparer** pour démarrer la réparation.  
  
    > [!TIP]  
    >  Si le Centre d'Installation a été lancé à l'aide du menu Démarrer, vous devez fournir l'emplacement actuel du support d'installation.  
  
4.  La règle de support d'installation et les routines de fichiers sont exécutées pour garantir que les composants requis sont installés sur votre système et que les règles de validation du programme d'installation ont été correctement exécutées sur l'ordinateur. Cliquez sur **OK** ou sur **Installer** pour continuer.  
  
5.  Dans la page Sélectionner une instance, sélectionnez l’instance à réparer, puis cliquez sur **Suivant** pour continuer.  
  
6.  Les règles de réparation sont exécutées pour valider l'opération. Pour continuer, cliquez sur **Suivant**.  
  
7.  La page Prêt à réparer indique que l'opération peut se poursuivre. Pour continuer, cliquez sur **Réparer**.  
  
8.  La page Progression de la réparation indique l'état de l'opération de réparation. La page Terminé indique que l'opération est terminée.  
  
### <a name="to-repair-a-failed-installation-of-includessnoversionincludesssnoversion-mdmd-using-command-prompt"></a>Pour réparer une installation défectueuse de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide de l'invite de commandes  
  
1.  À une invite de commandes, exécutez la commande suivante :  
  
    ```  
    Setup.exe /q /ACTION=Repair /INSTANCENAME=instancename  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et lire les fichiers journaux d'installation de SQL Server](view-and-read-sql-server-setup-log-files.md)   
 [Rubriques de procédures relatives à l’installation](../../sql-server/install/installation-how-to-topics.md)  
  
  