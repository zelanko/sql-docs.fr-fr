---
title: "Procédure pas à pas : Configurer SQL Server Integration Services avec montée en puissance | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 685286966599c4dcd3dc2f7029413c77f3ff2689
ms.openlocfilehash: c386b01043764405872365af379cfdedb036b65f
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="walkthrough-set-up-integration-services-scale-out"></a>Procédure pas à pas : Configurer Integration Services Scale Out
Configurer [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] monter en charge en effectuant les tâches suivantes. 

> [!NOTE]
> Si vous installez monter en charge sur un seul ordinateur, installez les fonctionnalités de mise à l’échelle des Master et de montée en puissance des processus de travail en même temps. Quand vous installez les fonctionnalités en même temps, le point de terminaison est généré automatiquement pour la connexion à Scale Out Master. 

* [Installer Scale Out Master](#InstallMaster)

* [Installer Scale Out Worker](#InstallWorker)

* [Installer le certificat client Scale Out Worker](#InstallCert)

* [Ouvrir le port de pare-feu](#Firewall)

* [Démarrer les services SQL Server Scale Out Master et Worker](#Start)

* [Activer Scale Out Master](#EnableMaster)

* [Activer le mode d’authentification SQL Server](#EnableAuth)

* [Activer Scale Out Worker](#EnableWorker)

## <a name="InstallMaster"></a> Installer Scale Out Master

Pour activer la fonctionnalité de mise à l’échelle des principale, vous devez installer les Services du moteur de base de données, [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)]et sa fonctionnalité de mise à l’échelle des principale lorsque vous configurez [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. 

Pour plus d’informations sur la configuration des services Moteur de base de données et d’[!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)], consultez [Installer le moteur de base de données SQL Server](../../database-engine/install-windows/install-sql-server-database-engine.md) et [Installer Integration Services](../install-windows/install-integration-services.md).
> [!NOTE]
> Pour utiliser le compte d’authentification SQL par défaut pour monter en charge de la journalisation, sélectionnez le Mode mixte pour le mode d’authentification sur la page de Configuration du moteur de base de données pendant l’installation du moteur de base de données. Consultez [modifier le compte pour la journalisation de monter en charge](change-logdb-account.md) pour plus d’informations.

**Pour installer la fonctionnalité Scale Out Master, utilisez l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ou l’invite de commandes.**

- Étapes pour l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]
  1.  Sur le **sélection des fonctionnalités** page, sélectionnez **échelle Out Master**, qui est répertorié sous [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  ![Sélection de la fonctionnalité Master](media/feature-select-master.PNG)
  
  2.  Dans la page **Configuration du serveur** , sélectionnez le compte pour exécuter le **service SQL Server Integration Services Scale Out Master** et sélectionnez le **Type de démarrage**.  
  ![Configuration de Serveur](media/server-config.PNG)
  3.  Dans la page **Configuration d’Integration Services Scale Out Master** , spécifiez le numéro de port utilisé par Scale Out Master pour communiquer avec Scale Out Worker. Le numéro de port par défaut est 8391.  
  ![Configuration de master](media/master-config.PNG "configuration de Master")
  4.  Spécifiez le certificat SSL utilisé pour protéger la communication entre l’échelle des principales et de montée en puissance des processus de travail en effectuant l’une des opérations suivantes.
    * Permettent de créer un certificat SSL auto-signé, par défaut en cliquant sur le processus d’installation **créer un nouveau certificat SSL**.  Le certificat par défaut est installé sous Autorités de certification racines de confiance, Ordinateur local. Vous pouvez spécifier les noms communs dans ce certificat. Le nom d’hôte du point de terminaison principal doit être inclus dans les noms communs. Par défaut, le nom de l’ordinateur et l’adresse ip du nœud de Master sont inclus.
    * Sélectionnez un certificats SSL existant sur l’ordinateur local en cliquant sur **utilise un certificat SSL existant** , puis en cliquant sur **Parcourir** pour sélectionner un certificat. L’empreinte numérique du certificat s’affiche dans la zone de texte. Cliquez sur **Parcourir** pour afficher les certificats stockés dans Autorités de certification racines de confiance, Ordinateur local. Le certificat que vous sélectionnez doit être stocké ici.       
![Configuration de master 2](media/master-config-2.PNG "Master configuration 2")
  5.  Terminez l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
- Étapes pour l’invite de commandes

    Suivez les instructions fournies dans [Installer SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Définissez les paramètres associés à Scale Out Master en procédant comme suit.
  1.  Ajoutez IS_Master au paramètre /FEATURES
  2.  Configurer l’échelle Out principale en spécifiant les paramètres suivants et leurs valeurs : /ISMASTERSVCACCOUNT, /ISMASTERSVCPASSWORD, /ISMASTERSVCSTARTUPTYPE, /ISMASTERSVCPORT, /ISMasterSVCSSLCertCN(optional), /ISMASTERSVCTHUMBPRINT(optional).

> [!Note]
> Si la mise à l’échelle des Master n’est pas installé avec le moteur de base de données et le moteur de base de données est une instance nommée, vous devez configurer SqlServerName dans le fichier de configuration de service de mise à l’échelle des Master après l’installation. Consultez [échelle Out Master](integration-services-ssis-scale-out-master.md) pour plus d’informations.

## <a name="InstallWorker"></a> Installer Scale Out Worker
 
Pour activer la fonctionnalité de Scale Out Worker, vous devez installer [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] et sa fonctionnalité Scale Out Worker dans le programme d’installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].

**Pour installer la fonctionnalité Scale Out Worker, utilisez l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ou l’invite de commandes.**

- Étapes pour l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]
  1.  Sur le **sélection des fonctionnalités** page, sélectionnez **montée en puissance des processus de travail**, qui est répertorié sous [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].   
  ![Sélection de la fonctionnalité Worker](media/feature-select-worker.PNG)
  2. Dans la page **Configuration du serveur** , sélectionnez le compte pour exécuter le **service SQL Server Integration Services Scale Out Worker** et sélectionnez le **Type de démarrage**.    
  ![Configuration du serveur 2](media/server-config-2.PNG "Server Configuration 2")
  3. Dans la page **Configuration d’Integration Services Scale Out Worker** , spécifiez le point de terminaison pour la connexion à Scale Out Master. 
      > [!Note]
      > Vous pouvez ignorer la configuration du nœud de travail (étapes 3 et 4) ici et associer le travailleur d’à l’échelle à l’échelle des maître avec [échelle Out Manager](integration-services-ssis-scale-out-manager.md) après l’installation.

    - Pour un **un seul ordinateur** environnement, le point de terminaison est générée automatiquement lors de la mise à l’échelle des principales et montée en puissance des processus de travail sont installés en même temps. 
    - Pour un **plusieurs ordinateurs** environnement, le point de terminaison se compose du nom ou adresse IP de l’ordinateur avec montée en puissance Out Master installé et le numéro de port spécifié pendant l’installation de la mise à l’échelle des Master.    
   ![Configuration de processus de travail 1](media/worker-config.PNG "Config de travail 1")    

  4. Pour un **plusieurs ordinateurs** environnement, spécifiez le certificat SSL client qui est utilisé pour valider la mise à l’échelle des Master. Pour un **un seul ordinateur** environnement, il est inutile de spécifier le certificat SSL client. 
  
     > [!NOTE]
     > Lorsque le certificat SSL utilisé par l’échelle Out maître est auto-signé, un certificat SSL de client correspondant est requis pour être installé sur l’ordinateur avec montée en puissance des processus de travail. Si vous fournissez le chemin d’accès de fichier pour le certificat SSL du client sur le **Configuration Integration Services montée en puissance des processus de travail** page, le certificat sera automatiquement installé ; sinon, vous devez installer le certificat manuellement plus tard. 
     
     Cliquez sur **Parcourir** pour rechercher le fichier de certificat (*.cer). Pour utiliser le certificat SSL par défaut, sélectionnez le fichier SSISScaleOutMaster.cer situé dans \<lecteur\>: \Program Files\Microsoft SQL Server\140\DTS\Binn sur l’ordinateur sur lequel est installé l’échelle des principales.   
   ![Configuration de processus de travail 2](media/worker-config-2.PNG "Config de travail 2")
  5. Terminez l’Assistant Installation de [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
- Étapes pour l’invite de commandes

    Suivez les instructions fournies dans [Installer SQL Server à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Définissez les paramètres associés à Scale Out Worker en procédant comme suit.
    1.  Ajoutez IS_Worker au paramètre /FEATURES
    2. Configurer la montée en puissance des processus de travail en spécifiant les paramètres suivants et leurs valeurs : /ISWORKERSVCACCOUNT, /ISWORKERSVCPASSWORD, /ISWORKERSVCSTARTUPTYPE, /ISWORKERSVCMASTER(optional), /ISWORKERSVCCERT(optional).

 
## <a name="InstallCert"></a> Installer le certificat client Scale Out Worker

Pendant l’installation de mise à l’échelle des processus de travail, un certificat de travail est automatiquement créé et installé sur l’ordinateur. Un certificat client correspondant, SSISScaleOutWorker.cer, est aussi installé sous \<lecteur\>:\Program Files\Microsoft SQL Server\140\DTS\Binn. Pour l’échelle des maître authentifier le montée en puissance des processus de travail, vous devez ajouter ce certificat client dans le magasin racine de l’ordinateur local avec montée en puissance Out maître.
  
Pour ajouter le certificat client au magasin racine, double-cliquez sur le fichier .cer et cliquez sur **Installer le certificat** dans la boîte de dialogue Certificat. L’ **Assistant Importation de certificat** s’affiche.  

## <a name="Firewall"></a> Ouvrir le port de pare-feu

Ouvrir le port spécifié pendant l’installation de mise à l’échelle des principale et le port du serveur SQL Server (1433 par défaut), à l’aide de pare-feu Windows sur l’ordinateur de l’échelle des principales.
    
## <a name="Start"></a> Démarrer les services SQL Server Scale Out Master et Worker

Si le type de démarrage des services n’est pas défini sur automatique lors de l’installation, démarrez les services : SQL Server Integration Services échelle Out Master 14.0 (SSISScaleOutMaster140) et SQL Server Integration Services échelle Out travail 14.0 (SSISScaleOutWorker140). 

> [!Note]
> Après avoir ouvert le port du pare-feu, vous devez également redémarrer le service de mise à l’échelle des processus de travail.
   
## <a name="EnableMaster"></a> Activer Scale Out Master

Cliquez sur **Activer ce serveur comme SSIS Scale Out Master** dans la boîte de dialogue **Créer un catalogue** quand vous créez le catalogue SSISDB dans [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../../includes/ssmanstudio-md.md)]. Ou bien, échelle Out Master peut être activée avec [échelle Out Manager](integration-services-ssis-scale-out-manager.md) après la création de catalogue.

## <a name="EnableAuth"></a> Activer le mode d’authentification SQL Server
Si [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] l’authentification n’est pas activée lors de l’installation du moteur de base de données, activer le mode d’authentification SQL Server sur le [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] instance qui héberge le catalogue SSIS. 

L’exécution des packages n’est pas bloquée quand l’authentification SQL Server est désactivée. Toutefois, le journal d’exécution ne peut pas écrire dans SSISDB.

## <a name="EnableWorker"></a> Activer Scale Out Worker

Montée en puissance des processus de travail peut être activé via [échelle Out Manager](integration-services-ssis-scale-out-manager.md), qui fournit l’interface graphique utilisateur ; ou activées via la procédure stockée, consultez la section ci-dessous.

Pour activer Scale Out Worker, exécutez la procédure stockée *[catalog].[enable_worker_agent]* avec **WorkerAgentId** comme paramètre. 

Vous obtenez la valeur de **WorkerAgentId** à partir de la vue de base de données *[catalog].[worker_agents]* dans SSISDB, une fois que Scale Out Worker est inscrit auprès de Scale Out Master. L’inscription prend plusieurs minutes une fois que les services Scale Out Master et Worker sont démarrés.

#### <a name="example"></a>Exemple
Cet exemple active le montée en puissance des processus de travail sur computerA.
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
La configuration de la fonctionnalité Scale Out est terminée. Vous pouvez maintenant exécuter des packages de monter en charge. Pour plus d’informations, consultez [Exécuter des packages dans Integration Services (SSIS) Scale Out](run-packages-in-integration-services-ssis-scale-out.md).
