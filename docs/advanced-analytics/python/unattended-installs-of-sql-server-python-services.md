---
title: "Installation sans assistance de Python Machine Learning Services (de-de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: "1"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 77d9a8fcaca2aa8161d6763cda74239754da41d5
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="unattended-installation-of-python-machine-learning-services-in-database"></a>Installation sans assistance de Python Machine Learning Services (de-de base de données)

Cette rubrique décrit comment utiliser les arguments de ligne de commande dans le programme d’installation de SQL Server 2017 pour installer le moteur de base de données SQL Server avec les Services de Machine Learning et Python, à l’aide du mode silencieux.

> [!NOTE]
> N’oubliez pas d’inclure les arguments de ligne de commande pour les contrats de licence, un pour Python et pour SQL Server.

## <a name="prerequisites"></a>Conditions préalables

Avant de lancer le processus d’installation, prenez connaissance des conditions requises suivantes :

+ Le service de Python ne peut pas être installé indépendamment le moteur de base de données SQL Server 2017. Vous devez inclure la fonctionnalité du moteur de base de données SQL.
+ Si vous effectuez une installation hors connexion, vous devez télécharger les composants requis de Python à l’avance et les copier dans un dossier local. Pour les emplacements de téléchargement, consultez [installation des composants Machine Learning sans accès à Internet](../../advanced-analytics/r-services/installing-ml-components-without-internet-access.md).
+ Il existe un nouveau paramètre, */IACCEPTPYTHONLICENSETERMS*, qui indique que vous avez accepté les termes du contrat de licence pour utiliser les composants de Python fournis par le Continuum Analytique. Si vous n’incluez pas ce paramètre dans la ligne de commande, l’installation échoue.
+ Pour terminer l’installation sans avoir à répondre aux invites, assurez-vous que vous avez identifié tous les arguments requis, y compris celles pour Python et la gestion de licences de SQL Server et pour toutes les autres fonctionnalités que vous souhaitez installer.
+  Mode d’authentification mixte était requis dans certaines versions préliminaires de SQL Server 2016. Il n’est plus nécessaire, alors qu’elle peut être utile dans les scénarios où les chercheurs de données sont développer et tester des solutions à distance à l’aide de connexions SQL.

## <a name="perform-an-unattended-installation-of-python-machine-learning-services-in-database"></a>Effectuer une installation sans assistance de Python Machine Learning Services (de-de base de données)

L’exemple suivant illustre la **minimale** requise des fonctionnalités à spécifier dans la ligne de commande lorsque vous effectuez une installation sans assistance de Python et le moteur de base de données sur l’instance par défaut.

> [!NOTE]
> Cette fonctionnalité nécessite SQL Server 2017. Python n’est pas pris en charge dans les versions antérieures de SQL Server.

1. Ouvrez une invite de commandes avec élévation de privilèges et exécutez la commande suivante :

    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONLICENSETERMS
    ```

    > [!NOTE]
    > 
    > Il existe de nouveaux indicateurs de programme d’installation de Python : `SQL_INST_MPY` et`IACCEPTPYTHONLICENSETERMS`

2. Redémarrez le serveur, comme indiqué.
3. Effectuez les étapes de configuration post-installation comme indiqué dans [cette section](#bkmk_PostInstall). Un autre redémarrage des services SQL Server sera nécessaire.

## <a name = "bkmk_PostInstall"></a>Étapes de post-installation

1.  Une fois l’installation terminée, ouvrez une nouvelle **requête** fenêtre dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], et exécutez la commande suivante pour activer la fonctionnalité.

    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  Vous devez explicitement activer la fonctionnalité de reconfigurer ; dans le cas contraire, il ne sera pas possible d’appeler des scripts externes même si la fonctionnalité a été installée.
  
3.  Redémarrez le service SQL Server pour l’instance reconfiguré. Cette opération redémarre automatiquement le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ainsi le service.

3. D’autres étapes peuvent être nécessaires si vous avez une configuration de sécurité personnalisée ou si vous prévoyez d’utiliser SQL Server pour prendre en charge des contextes de calcul à distance. Pour plus d’informations, consultez [résolution des problèmes d’installation de la machine learning](../machine-learning-troubleshooting-faq.md).
