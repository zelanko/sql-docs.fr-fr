---
title: Installation sans assistance de Machine Learning Services | Documents Microsoft
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 18
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: babb74aa866404853cfef83e1d30159354f385e7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="unattended-installation-of-machine-learning-services-in-database"></a>Installation sans assistance de Machine Learning Services (de-de base de données)

Cette rubrique décrit comment utiliser des arguments de ligne de commande avec le programme d’installation de SQL Server pour installer l’apprentissage automatique dans une instance du moteur de base de données, en mode silencieux. Dans une installation sans assistance, vous n’utilisez pas les fonctionnalités interactives de l’Assistant Installation et devez fournir tous les arguments requis pour terminer l’installation, y compris pour SQL Server et pour les composants d’apprentissage machine de contrats de licence.

**S’applique à :** SQL Server 2016 R Services, SQL Server 2017 d’apprentissage Services (de-de base de données)

> [!IMPORTANT]
> 
> Dans SQL Server 2016 et SQL Server 2017, les étapes supplémentaires sont nécessaires une fois le programme d’installation est terminée pour activer la fonctionnalité. Ceux-ci incluent une reconfiguration et le redémarrage de l’instance. Veillez à consulter toutes les étapes.

## <a name="prerequisites"></a>Conditions préalables

+ Vous devez installer le moteur de base de données sur chaque instance dans laquelle vous allez utiliser l’apprentissage automatique.

+ Si l’ordinateur n’a pas accès à Internet, veillez à installer les programmes d’installation pour l’apprentissage automatique des composants au préalable. Pour les emplacements de téléchargement, consultez [l’installation des composants d’apprentissage machine sans accès à Internet](../../advanced-analytics/r/installing-ml-components-without-internet-access.md).

+ Il existe de nouvelles licences paramètres liés aux composants open source pour R et Python. Vous devez accepter les termes du contrat de licence avec un argument distinct pour chaque langue que vous installez. Si vous n’incluez pas ce paramètre dans la ligne de commande, l’installation échoue.

+ Pour terminer l’installation sans avoir à répondre aux invites, assurez-vous que vous avez identifié tous les arguments requis, y compris celles des licences et pour toutes les autres fonctionnalités que vous souhaitez installer.

> [!NOTE] 
> Le mode de sécurité mixte qui prend en charge les connexions SQL était requis dans les premières versions. Toutefois, vous pouvez envisager d’activer l’authentification en Mode mixte prendre en charge le développement de solutions par les spécialistes de données à l’aide d’une connexion SQL.

## <a name="bkmk_NewInstall"></a>Installation sans assistance de Machine Learning Services avec R

L’exemple suivant illustre la **minimale** installent des fonctionnalités requises à spécifier dans la ligne de commande lors de l’exécution en mode silencieux, sans assistance de SQL Server 2017 Machine Services (de-de base de données).

1. Ouvrez une invite de commandes avec élévation de privilèges et exécutez la commande suivante :

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
    ```
    
    Notez les indicateurs nécessaires pour R dans SQL Server 2017 : `ADVANCEDANALYTICS`, `SQL_INST_MR`, et `IACCEPTROPENLICENSETERMS`.
2. Redémarrez le serveur.
3. Effectuez les étapes de configuration post-installation comme indiqué dans [cette section](#bkmk_PostInstall). Un autre redémarrage des services SQL Server sera nécessaire.

## <a name="OldInstall"></a>Installation sans assistance de R Services (de-de base de données)
 
 L’exemple suivant illustre la **minimale** installent des fonctionnalités requises à spécifier dans la ligne de commande lors de l’exécution en mode silencieux, sans assistance de SQL Server 2016 R Services.

1. Ouvrez une invite de commandes avec élévation de privilèges et exécutez la commande suivante :

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
    ```
    Notez les indicateurs requis pour les SERVICES de R 2016 : `ADVANCEDANALYTICS` et `IACCEPTROPENLICENSETERMS`.
2. Redémarrez le serveur.
3. Effectuez les étapes de configuration post-installation comme indiqué dans [cette section](#bkmk_PostInstall). Un autre redémarrage des services SQL Server sera nécessaire.

## <a name = "bkmk_PostInstall"></a>Étapes supplémentaires après l’installation

1.  Une fois l’installation terminée, ouvrez une nouvelle **requête** fenêtre dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], et exécutez la commande suivante pour activer la fonctionnalité.
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  Vous devez explicitement activer la fonctionnalité de reconfigurer ; dans le cas contraire, il ne sera pas possible d’appeler des scripts externes même si la fonctionnalité a été installée.
  
2.  Redémarrez le service SQL Server pour l’instance reconfiguré. Cette opération redémarre automatiquement le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ainsi le service.

3. D’autres étapes peuvent être nécessaires si vous avez une configuration de sécurité personnalisée ou si vous prévoyez d’utiliser SQL Server pour prendre en charge des contextes de calcul à distance. Pour plus d’informations, consultez [Questions fréquentes sur l’installation et la mise à niveau](../../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md).

