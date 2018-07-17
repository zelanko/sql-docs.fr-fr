---
title: Résoudre les problèmes de l’utilitaire SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
caps.latest.revision: 8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 81b35d1af874c97bf2e61e9c1234d7ad7876e229
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37328139"
---
# <a name="troubleshoot-the-sql-server-utility"></a>Résolution des problèmes liés à l’utilitaire SQL Server
  Les problèmes à résoudre liés à l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peuvent inclure la résolution d'une opération ayant échoué d'inscription d'une instance de SQL Server avec un UCP, de l'échec de la collecte de données qui grise des icônes dans le mode Liste de l'instance gérée sur un UCP, l'atténuation des goulots d'étranglement des performances, ou la résolution des problèmes d'intégrité des ressources. Pour plus d’informations sur l’atténuation des problèmes d’intégrité de ressource identifiées par un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP, consultez [résoudre les problèmes de SQL Server Resource Health &#40;utilitaire SQL Server&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md).  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a>Opération d'inscription d'une instance de SQL Server dans un utilitaire SQL Server ayant échoué  
 Si vous vous connectez à l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à inscrire à l’aide [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l’authentification et que vous spécifiez un compte proxy qui appartient à un domaine Active Directory autre que le domaine où se trouve l’UCP, validation d’instance réussit, mais le opération d’inscription échoue avec le message d’erreur suivant :  
  
 Une exception s'est produite lors de l'exécution d'une instruction ou d'un lot Transact-SQL ou lot. (Microsoft.SqlServer.ConnectionInfo)  
  
 Informations supplémentaires : Impossible d’obtenir des informations sur l’utilisateur ou le groupe Windows NT « \<Nom_Domaine\Nom_Compte> », code d’erreur 0x5. (Microsoft SQL Server, erreur : 15404)  
  
 Dans ce scénario d'exemple, vous pouvez rencontrer le problème suivant :  
  
1.  L'UCP est un membre de « Domain_1 ».  
  
2.  Une relation d'approbation de domaine unidirectionnelle est en place : autrement dit, « Domain_1 » n'est pas approuvé par « Domain_2 » mais « Domain_2 » est approuvé par « Domain_1 ».  
  
3.  L'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à inscrire dans l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est également un membre de « Domain_1 ».  
  
4.  Lors de l'opération d'inscription, connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour procéder à l'inscription en utilisant « sa ». Spécifiez un compte proxy de « Domain_2 ».  
  
5.  La validation réussit mais l'inscription échoue.  
  
 La solution de contournement pour ce problème, dans l'exemple ci-dessus, consiste à se connecter à l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour l'inscrire dans l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l'aide de « sa » et fournir un compte proxy de « Domain_1 ».  
  
## <a name="failed-wmi-validation"></a>Échec de validation WMI  
 Si WMI n'est pas configuré correctement sur une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], les opérations Créer un UCP et Inscrire une instance gérée affichent un avertissement, mais l'opération n'est pas bloquée. En outre, si vous modifiez le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration de compte de l’Agent afin que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent n’est pas autorisé pour les classes WMI obligatoire, collecte de données sur l’instance gérée affecté de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne parvient pas à charger sur l’UCP. Cela provoque des icônes grises dans l'UCP.  
  
 L'échec de la collecte de données provoque des icônes d'état grises en mode Liste de l'UCP pour les instances managées affectées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. L'historique des travaux sur l'instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] indique un échec de sysutility_mi_collect_and_upload à l'étape 2 (Données d'étape collectées à partir du script PowerShell).  
  
 Les messages d'erreur simplifiés sont les suivants :  
  
 L'exécution de la commande s'est arrêtée, car la variable d'environnement « ErrorActionPreference » a la valeur Stop : accès refusé.  
  
 Erreur : \<Date-heure (MM/jj/aaaa hh : mm :) > : exception interceptée lors de la collecte des propriétés de l’UC.  Une requête WMI a peut-être échoué.  AVERTISSEMENT.  
  
 Pour résoudre ce problème, vérifiez les paramètres de configuration suivants :  
  
-   Sur Windows Server 2003, le service SQL Server Agent doit faire partie du groupe d’analyse des performances de Windows sur l’instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Le service WMI doit être activé et configuré sur l'instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Le référentiel WMI est peut-être endommagé sur l’instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   La bibliothèque de performances peut être manquante ou endommagée sur l’instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Pour vérifier que l'instance spécifiée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est configurée correctement sur les données de rapport de l'UCP, vérifiez que les classes suivantes sont disponibles sur l'instance spécifiée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], et qu'elles sont accessibles au compte de service Agent SQL Server :  
  
-   Win32_MountPoint  
  
-   Win32_PerfRawData_PerfProc_Process  
  
-   Win32_PerfRawData_PerfOS_Processor  
  
-   Win32_Processor  
  
-   Win32_Volume  
  
-   Win32_LogicalDisk  
  
 Vous pouvez utiliser l'applet de commande PowerShell de get-WmiObject sur chacune des classes pour vérifier que chaque classe est accessible. Exécuter les applets de commande suivantes sur l’instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 Pour plus d'informations sur la résolution des problèmes liés à WMI, consultez [Dépannage de WMI](http://go.microsoft.com/fwlink/?LinkId=178250). Notez que les requêtes dans ces opérations de l'utilitaire SQL Server s'exécutent localement, donc le DCOM et le contenu de résolution des problèmes à distance ne s'appliquent pas.  
  
## <a name="failed-data-collection"></a>Échec de la collecte de données  
 Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] utilitaire les événements de collecte de données échouent, envisagez les possibilités suivantes :  
  
-   Ne modifiez pas les propriétés du jeu d'éléments de collecte « Informations sur l'utilitaire » sur une instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], et n'activez pas ou ne désactivez pas manuellement la collecte de données, car la collecte de données est contrôlée par un travail d'agent Utilitaire.  
  
-   Validation WMI ayant échoué ou non prise en charge. Pour plus d'informations, consultez la section « Échec de validation VMI », plus haut dans cette rubrique.  
  
-   Actualiser les données dans la vue instance managée, en tant que données dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] points de vue utilitaire n’est pas actualisée automatiquement. Pour actualiser les données, cliquez sur le **Instances gérées** nœud dans le **Navigation de l’Explorateur de l’utilitaire** volet, puis sélectionnez **Actualiser**, ou avec le bouton droit sur le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nom dans la liste de l’instance, puis sélectionnez **Actualiser**. Notez qu'une fois qu'une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a été inscrite avec un UCP, cela peut prendre jusqu'à 30 minutes pour que les données s'affichent d'abord dans le tableau de bord et les points de vue dans le volet Contenu de l'Explorateur de l'utilitaire.  
  
-   Utilisez le Gestionnaire de Configuration SQL Server pour vérifier que l’instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est en cours d’exécution.  
  
-   Si la collecte ou le téléchargement de données échouent en raison de problèmes de délais d'attente, mettez à jour la fonction dbo.fn_sysutility_mi_get_collect_script() dans la base de données MSDB. Plus particulièrement, dans la fonction Invoke-BulkCopyCommand(), ajoutez la ligne :  
  
    ```  
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     La valeur de délai d'attente par défaut est de 30 secondes.  
  
-   Si l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'est pas un cluster, vérifiez que le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent s'exécute et que le service est configuré pour démarrer automatiquement sur l'UCP et sur l'instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
-   Vérifiez qu’un compte valide est utilisé pour exécuter la collecte de données sur l’instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Par exemple, le mot de passe a pu expirer. Si le mot de passe du proxy a expiré, mettez à jour les informations d'identification relatives au mot de passe dans SSMS, comme suit :  
  
    1.  Dans SSMS **Explorateur d'objets**, développez le nœud **Sécurité** , puis le nœud **Informations d'identification** .  
  
    2.  Avec le bouton droit sur **UtilityAgentProxyCredential_\<GUID >** et sélectionnez **propriétés**.  
  
    3.  Dans la boîte de dialogue Propriétés des informations d’identification, les informations d’identification nécessaires pour mettre à jour le **UtilityAgentProxyCredential_\<GUID >** informations d’identification.  
  
    4.  Cliquez sur **OK** pour confirmer la modification.  
  
-   TCP/IP doit être activé sur l’UCP et sur l’instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Activez TCP/IP via [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager.  
  
-   Le service SQL Server Browser sur l'UCP doit être démarré et configuré pour démarrer automatiquement. Si votre organisation empêche d'utiliser le service SQL Server Browser, utilisez la procédure suivante pour autoriser une instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à se connecter à l'UCP :  
  
    1.  Dans la barre des tâches de Windows sur l’instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], cliquez sur **Démarrer**, puis cliquez sur **exécuter...** .  
  
    2.  Tapez « cliconfg.exe » dans l'espace fourni, puis cliquez sur **OK**.  
  
    3.  Si vous êtes invités à autoriser « SQL Client Configuration Utility EXE » à démarrer, cliquez sur «**Continuer**».  
  
    4.  Dans la boîte de dialogue **Utilitaire réseau du client SQL Server** , sélectionnez l'onglet **Alias** , puis cliquez sur **Ajouter…**.  
  
    5.  Dans la boîte de dialogue **Ajouter la nouvelle configuration de la bibliothèque réseau** :  
  
    6.  Spécifiez TCP/IP dans la liste des bibliothèques réseau.  
  
    7.  Spécifiez le ComputerName\InstanceName de l'UCP dans la zone de texte **Alias du serveur** .  
  
    8.  Spécifiez le ComputerName de l'UCP dans la zone de texte **Nom du serveur** .  
  
    9. Désactivez la case à cocher **Déterminer le port de manière dynamique** .  
  
    10. Spécifiez le numéro de port que l'UCP écoute dans la zone de texte **Numéro du port** .  
  
    11. Cliquez sur **OK** pour enregistrer vos modifications.  
  
    12. Répétez ces étapes pour chaque instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui se connecte à un UCP où le service SQL Server Browser n’est pas activé.  
  
-   Vérifiez que les instances de managées [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont connectés au réseau.  
  
-   S'il existe des bases de données avec le même nom mais des paramètres différents de sensibilité à la casse sur une instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], l'identification entre la base de données et ses points de vue peut être incorrecte, ce qui provoque un échec de la collecte de données. Par exemple, une base de données nommée « MYDATABASE » peut afficher des états d'intégrité pour une base de données nommée « MyDatabase ». Aucune erreur n'est générée dans ce scénario. L'échec de la collecte de données peut également résulter du non respect de la casse dans d'autres objets affichés dans l'UCP, comme fichier de base de données et les noms de groupes de fichiers.  
  
-   Si une instance managée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est hébergée sur un ordinateur Windows Server 2003, le compte du service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent doit appartenir au groupe de sécurité Utilisateurs de l'Analyseur de performances ou au groupe local Administrateurs. Sinon, la collecte de données échouera avec une erreur d'accès refusé. Pour ajouter un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] compte de service Agent au groupe de sécurité utilisateurs de moniteur de performances, procédez comme suit :  
  
    1.  Ouvrez **Gestion de l'ordinateur**, puis **Utilisateurs et groupes locaux**, puis **Groupes**.  
  
    2.  Cliquez avec le bouton droit sur **Utilisateurs de l'Analyseur de performances** et sélectionnez **Ajouter au groupe**.  
  
    3.  Cliquez sur **Ajouter**.  
  
    4.  Entrez le compte sous lequel le service Agent SQL Server s'exécute, puis cliquez sur **OK**.  
  
    5.  Si l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a déjà été inscrite avec l'UCP avant d'ajouter l'utilisateur à ce groupe, redémarrez le service [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités et tâches de l'utilitaire SQL Server](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Résoudre les problèmes de contrôle d’intégrité de SQL Server &#40;utilitaire SQL Server&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)  
  
  
