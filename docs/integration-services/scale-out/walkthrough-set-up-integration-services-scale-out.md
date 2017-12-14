---
title: "Procédure pas à pas : Configurer SQL Server Integration Services Scale Out | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ec9744a1efb0e78aca55e85e7f9f3eca007de5a2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="walkthrough-set-up-integration-services-scale-out"></a>Procédure pas à pas : Configurer Integration Services Scale Out
Configurez [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] Scale Out en effectuant les tâches suivantes. 

> [!NOTE]
> Si vous installez Scale Out sur un seul ordinateur, installez les fonctionnalités Scale Out Master et Scale Out Worker en même temps. Quand vous installez les fonctionnalités en même temps, le point de terminaison est généré automatiquement pour la connexion à Scale Out Master. 

* [Installer Scale Out Master](#InstallMaster)

* [Installer Scale Out Worker](#InstallWorker)

* [Installer le certificat client Scale Out Worker](#InstallCert)

* [Ouvrir le port de pare-feu](#Firewall)

* [Démarrer les services SQL Server Scale Out Master et Worker](#Start)

* [Activer Scale Out Master](#EnableMaster)

* [Activer le mode d’authentification SQL Server](#EnableAuth)

* [Activer Scale Out Worker](#EnableWorker)

## <a name="InstallMaster"></a> Installer Scale Out Master

Pour activer la fonctionnalité de Scale Out Master, vous devez installer les services Moteur de base de données, [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] et sa fonctionnalité Scale Out Master quand vous configurez [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. 

Pour plus d’informations sur la configuration des services Moteur de base de données et d’[!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)], consultez [Installer le moteur de base de données SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md) et [Installer Integration Services](../install-windows/install-integration-services.md).
> [!NOTE]
> Pour utiliser le compte d’authentification SQL par défaut pour la journalisation Scale Out, sélectionnez le mode mixte comme mode d’authentification dans la page Configuration du moteur de base de données pendant l’installation du moteur de base de données. Consultez [Changer le compte pour la journalisation Scale Out](change-logdb-account.md) pour plus d’informations.

**Pour installer la fonctionnalité Scale Out Master, utilisez l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ou l’invite de commandes.**

- Étapes pour l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]
  1.  Dans la page **Sélection de fonctionnalités**, choisissez **Scale Out Master** sous [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  ![Sélection de la fonctionnalité Master](media/feature-select-master.PNG)
  
  2.  Dans la page **Configuration du serveur** , sélectionnez le compte pour exécuter le **service SQL Server Integration Services Scale Out Master** et sélectionnez le **Type de démarrage**.  
  ![Configuration de Serveur](media/server-config.PNG)
  3.  Dans la page **Configuration d’Integration Services Scale Out Master** , spécifiez le numéro de port utilisé par Scale Out Master pour communiquer avec Scale Out Worker. Le numéro de port par défaut est 8391.  
  ![Configuration de Master](media/master-config.PNG "Configuration de Master")
  4.  Spécifiez le certificat SSL utilisé pour protéger les communications entre Scale Out Master et Scale Out Worker en effectuant l’une des opérations suivantes.
    * Laissez le processus d’installation créer un certificat SSL auto-signé par défaut en cliquant sur **Créer un certificat SSL**.  Le certificat par défaut est installé sous Autorités de certification racines de confiance, Ordinateur local. Vous pouvez spécifier les noms communs dans ce certificat. Le nom d’hôte du point de terminaison principal doit être inclus dans les noms communs. Par défaut, le nom de machine et l’adresse IP du nœud Master sont inclus.
    * Sélectionnez un certificat SSL existant sur l’ordinateur local en cliquant sur **Utiliser un certificat SSL existant**, puis en cliquant sur **Parcourir** pour sélectionner un certificat. L’empreinte numérique du certificat s’affiche dans la zone de texte. Cliquez sur **Parcourir** pour afficher les certificats stockés dans Autorités de certification racines de confiance, Ordinateur local. Le certificat que vous sélectionnez doit être stocké ici.       
![Configuration de Master 2](media/master-config-2.PNG "Configuration de Master 2")
  5.  Terminez l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
- Étapes pour l’invite de commandes

    Suivez les instructions fournies dans [Installer SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Définissez les paramètres associés à Scale Out Master en procédant comme suit.
  1.  Ajoutez IS_Master au paramètre /FEATURES
  2.  Configurez Scale Out Master en spécifiant les paramètres suivants et leurs valeurs : /ISMASTERSVCACCOUNT, /ISMASTERSVCPASSWORD, /ISMASTERSVCSTARTUPTYPE, /ISMASTERSVCPORT, /ISMasterSVCSSLCertCN(facultatif), /ISMASTERSVCTHUMBPRINT(facultatif).

> [!Note]
> Si Scale Out Master n’est pas installé avec le moteur de base de données et que celui-ci est une instance nommée, vous devez configurer SqlServerName dans le fichier de configuration du service Scale Out Master après l’installation. Pour plus d’informations, consultez [Scale Out Master](integration-services-ssis-scale-out-master.md).

## <a name="InstallWorker"></a> Installer Scale Out Worker
 
Pour activer la fonctionnalité de Scale Out Worker, vous devez installer [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] et sa fonctionnalité Scale Out Worker dans le programme d’installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

**Pour installer la fonctionnalité Scale Out Worker, utilisez l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ou l’invite de commandes.**

- Étapes pour l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]
  1.  Dans la page **Sélection de fonctionnalités**, choisissez **Scale Out Worker**, sous [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  ![Sélection de la fonctionnalité Worker](media/feature-select-worker.PNG)
  2. Dans la page **Configuration du serveur** , sélectionnez le compte pour exécuter le **service SQL Server Integration Services Scale Out Worker** et sélectionnez le **Type de démarrage**.    
  ![Configuration du serveur 2](media/server-config-2.PNG "Configuration du serveur 2")
  3. Dans la page **Configuration d’Integration Services Scale Out Worker** , spécifiez le point de terminaison pour la connexion à Scale Out Master. 
      > [!Note]
      > Vous pouvez ignorer la configuration du nœud worker (étapes 3 et 4) à ce stade et associer le Scale Out Worker à Scale Out Master avec [Scale Out Manager](integration-services-ssis-scale-out-manager.md) après l’installation.

    - Pour un environnement à **un seul ordinateur**, le point de terminaison est généré automatiquement quand Scale Out Master et Scale Out Worker sont installés en même temps. 
    - Pour un environnement **à plusieurs ordinateurs**, le point de terminaison se compose du nom ou de l’adresse IP de l’ordinateur où Scale Out Master est installé et du numéro de port spécifié pendant l’installation de Scale Out Master.    
   ![Configuration de Worker 1](media/worker-config.PNG "Configuration de Worker 1")    

  4. Pour un environnement **à plusieurs ordinateurs**, spécifiez le certificat client SSL utilisé pour valider Scale Out Master. Pour un environnement à **un seul ordinateur**, il est inutile de spécifier le certificat client SSL. 
  
     > [!NOTE]
     > Quand le certificat SSL utilisé par Scale Out Master est auto-signé, un certificat client SSL correspondant doit être installé sur l’ordinateur Scale Out Worker. Si vous fournissez le chemin de fichier du certificat client SSL dans la page **Configuration d’Integration Services Scale Out Worker**, le certificat est installé automatiquement. Sinon, vous devez installer le certificat manuellement plus tard. 
     
     Cliquez sur **Parcourir** pour rechercher le fichier de certificat (*.cer). Pour utiliser le certificat SSL par défaut, sélectionnez le fichier SSISScaleOutMaster.cer situé sous \<lecteur\>:\Program Files\Microsoft SQL Server\140\DTS\Binn sur l’ordinateur où Scale Out Master est installé.   
   ![Configuration de Worker 2](media/worker-config-2.PNG "Configuration de Worker 2")
  5. Terminez l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
- Étapes pour l’invite de commandes

    Suivez les instructions fournies dans [Installer SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Définissez les paramètres associés à Scale Out Worker en procédant comme suit.
    1.  Ajoutez IS_Worker au paramètre /FEATURES
    2. Configurez Scale Out Worker en spécifiant les paramètres suivants et leurs valeurs : /ISWORKERSVCACCOUNT, /ISWORKERSVCPASSWORD, /ISWORKERSVCSTARTUPTYPE, /ISWORKERSVCMASTER(facultatif), /ISWORKERSVCCERT(facultatif).

 
## <a name="InstallCert"></a> Installer le certificat client Scale Out Worker

Pendant l’installation de Scale Out Worker, un certificat de Worker est créé et installé automatiquement sur l’ordinateur. Un certificat client correspondant, SSISScaleOutWorker.cer, est aussi installé sous \<lecteur\>:\Program Files\Microsoft SQL Server\140\DTS\Binn. Pour que Scale Out Master authentifie Scale Out Worker, vous devez ajouter ce certificat client au magasin racine de l’ordinateur local où Scale Out Master est installé.
  
Pour ajouter le certificat client au magasin racine, double-cliquez sur le fichier .cer et cliquez sur **Installer le certificat** dans la boîte de dialogue Certificat. L’ **Assistant Importation de certificat** s’affiche.  

## <a name="Firewall"></a> Ouvrir le port de pare-feu

Ouvrez le port spécifié pendant l’installation de Scale Out Master et le port de SQL Server (1433, par défaut) à l’aide du Pare-feu Windows sur l’ordinateur Scale Out Master.
    
## <a name="Start"></a> Démarrer les services SQL Server Scale Out Master et Worker

Si le type de démarrage des services n’est pas automatique pendant l’installation, démarrez les services SQL Server Integration Services Scale Out Master 14.0 (SSISScaleOutMaster140) et SQL Server Integration Services Scale Out Worker 14.0 (SSISScaleOutWorker140). 

> [!Note]
> Après avoir ouvert le port du pare-feu, vous devez également redémarrer le service Scale Out Worker.
   
## <a name="EnableMaster"></a> Activer Scale Out Master

Cliquez sur **Activer ce serveur comme SSIS Scale Out Master** dans la boîte de dialogue **Créer un catalogue** quand vous créez le catalogue SSISDB dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../../includes/ssmanstudio-md.md)]. Vous pouvez également activer Scale Out Master avec [Scale Out Manager](integration-services-ssis-scale-out-manager.md) une fois le catalogue créé.

## <a name="EnableAuth"></a> Activer le mode d’authentification SQL Server
Si l’authentification [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] n’est pas activée pendant l’installation du moteur de base de données, activez le mode d’authentification SQL Server sur l’instance de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] qui héberge le catalogue SSISDB. 

L’exécution des packages n’est pas bloquée quand l’authentification SQL Server est désactivée. Toutefois, le journal d’exécution ne peut pas écrire dans SSISDB.

## <a name="EnableWorker"></a> Activer Scale Out Worker

Scale Out Worker peut être activé par le biais de [Scale Out Manager](integration-services-ssis-scale-out-manager.md), qui fournit une interface graphique utilisateur, ou d’une procédure stockée (voir ci-après).

Pour activer Scale Out Worker, exécutez la procédure stockée *[catalog].[enable_worker_agent]* avec **WorkerAgentId** comme paramètre. 

Vous obtenez la valeur de **WorkerAgentId** à partir de la vue de base de données *[catalog].[worker_agents]* dans SSISDB, une fois que Scale Out Worker est inscrit auprès de Scale Out Master. L’inscription prend plusieurs minutes une fois que les services Scale Out Master et Worker sont démarrés.

#### <a name="example"></a>Exemple
Cet exemple active Scale Out Worker sur computerA.
```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName  --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    computerA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```
## <a name="next-steps"></a>Étapes suivantes
La configuration de la fonctionnalité Scale Out est terminée. Vous pouvez maintenant exécuter des packages dans Scale Out. Pour plus d’informations, consultez [Exécuter des packages dans Integration Services (SSIS) Scale Out](run-packages-in-integration-services-ssis-scale-out.md).
