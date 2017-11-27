---
title: Installation sans assistance de Machine Learning Services | Documents Microsoft
ms.custom: 
ms.date: 10/31/2017
ms.prod:
- sql-server-2016
- sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: "18"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: c58bbb4a7277b37c9ef479b79ba4809a02218908
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="unattended-installation-of-machine-learning-services-in-database"></a>Installation sans assistance de Machine Learning Services (de-de base de données)

Cet article décrit comment utiliser des arguments de ligne de commande avec le programme d’installation de SQL Server pour installer les composants d’apprentissage automatique.

Par une installation sans assistance, nous entendons ne pas utiliser les fonctionnalités interactives de l’Assistant Installation et de fournir à la place de tous les arguments requis pour terminer l’installation, y compris les licences des contrats pour SQL Server et pour les composants d’apprentissage machine sur un ligne de commande ou dans le cadre d’un script, généralement en mode silencieux.

+ [SQL Server 2016 R Services](#bkmk_OldInstall)
+ [L’ordinateur SQL Server 2017 Learning Services](#bkmk_NewInstall) avec R ou Python
+ [Microsoft R Server ou serveur de Machine Learning](../r/install-microsoft-r-server-from-the-command-line.md)

**S’applique à : SQL Server 2017 Machine Learning Services (de-de base de données), SQL Server 2016 R Services**

## <a name="prerequisites"></a>Conditions préalables

+ Vous devez installer le moteur de base de données sur chaque instance dans laquelle vous allez utiliser l’apprentissage automatique.

+ Si l’ordinateur n’a pas accès à Internet, veillez à télécharger les programmes d’installation pour l’apprentissage automatique des composants au préalable. Consultez [l’installation des composants d’apprentissage machine sans accès à Internet](../r/installing-ml-components-without-internet-access.md).

+ Il sont distincts de licences des paramètres pour chacun des composants open source pour R et Python. SQL Server 2016 prend en charge uniquement R ; SQL Server 2017 prend en charge R et Python. Vous devez accepter les termes du contrat de licence pour chaque langue que vous installez. Le programme d’installation échoue si vous n’incluez pas ce paramètre dans votre ligne de commande.

+ Pour terminer l’installation sans avoir à répondre aux invites, assurez-vous que vous avez identifié tous les arguments requis, y compris celles des licences et pour toutes les autres fonctionnalités que vous souhaitez installer.

+ Le **mixte** mode de sécurité qui prend en charge les connexions SQL était nécessaire dans les premières versions. Bien qu’il n’est plus nécessaire, vous pouvez envisager d’activer l’authentification en Mode mixte prendre en charge le développement de solutions par les spécialistes de données qui utilisent une connexion SQL.

> [!IMPORTANT]
> 
> Étapes supplémentaires sont nécessaires une fois le programme d’installation est terminée pour activer la fonctionnalité. Ceux-ci incluent une reconfiguration et le redémarrage de l’instance. Bien sûr pour passer en revue tous les éléments dans la section [étapes de post-installation] (#bkmk_PostInstall) pour déterminer les actions nécessaires une fois le programme d’installation est terminée.

## <a name="bkmk_NewInstall"></a>Installation de ligne de commande pour SQL Server 2017

Les exemples suivants incluent les **minimale** fonctionnalités requises.

> [!IMPORTANT]
> Veillez à exécuter toutes les commandes à partir d’une invite de commandes avec élévation de privilèges.
> 
> Une fois l’installation terminée, quelques étapes supplémentaires sont nécessaires. Consultez [cette section](#bkmk_PostInstall). 
> Un autre redémarrage des services SQL Server devront être réalisée une fois que la configuration est terminée.

### <a name="install-r-only"></a>Installation R

L’exemple suivant affiche les arguments requis pour exécuter en mode silencieux, sans assistance d’installation de SQL Server 2017 Machine Services (de-de base de données) avec le langage R ajouté.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

Notez les indicateurs nécessaires pour R dans SQL Server 2017 :

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MR`
+ `IACCEPTROPENLICENSETERMS`.

### <a name="install-python-only"></a>Installer uniquement les Python

L’exemple suivant affiche les arguments requis pour exécuter en mode silencieux, sans assistance d’installation de SQL Server 2017 Machine Services (de-de base de données) avec le langage Python ajouté.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

Notez les indicateurs nécessaires pour Python dans SQL Server 2017 :

+ `ADVANCEDANALYTICS`
+ `SQL_INST_MPY`
+ `IACCEPTPYTHONOPENLICENSETERMS`

### <a name="install-both-r-and-python-on-a-named-instance"></a>Installer R et Python sur une instance nommée

L’exemple suivant affiche les arguments requis pour exécuter en mode silencieux, sans assistance d’installation de SQL Server 2017 Machine Services (de-de base de données) sur une instance nommée. Langues R et Python sont ajoutés.

```
Setup.exe /q /ACTION=Install /FEATURES=SQLENGINE,ADVANCEDANALYTICS, SQL_INST_MR, SQL_INST_MPY /INSTANCENAME=MSSQLSERVER.ServerName /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS /IACCEPTPYTHONOPENLICENSETERMS
```

## <a name="OldInstall"></a>Installation de ligne de commande pour SQL Server 2016
 
L’exemple suivant affiche les arguments requis pour exécuter en mode silencieux, sans assistance d’installation de SQL Server 2016 avec le langage R ajouté.

```
Setup.exe /q /ACTION=Install /FEATURES=SQL,ADVANCEDANALYTICS /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS
```

Notez les indicateurs nécessaires pour 2016 R Services :

+ `ADVANCEDANALYTICS`
+ `IACCEPTROPENLICENSETERMS`

## <a name = "bkmk_PostInstall"></a>Étapes supplémentaires après l’installation

Vous devez effectuer les étapes suivantes après l’installation de SQL Server, quelle que soit la version que vous avez installé. fonctionnalités de machine learning ne sont pas activées par défaut et doivent être explicitement activées.

1.  Une fois l’installation terminée, ouvrez une nouvelle **requête** fenêtre dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], et exécutez la commande suivante pour activer la fonctionnalité.
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
    > [!NOTE]
    >  Vous devez explicitement activer la fonctionnalité de reconfigurer ; dans le cas contraire, il ne sera pas possible d’appeler des scripts externes même si la fonctionnalité a été installée.
  
2.  Redémarrez le service SQL Server pour l’instance reconfiguré. Cette opération redémarre automatiquement le [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ainsi le service.

> [!IMPORTANT]
> 
> Des étapes supplémentaires peuvent être requis si vous avez une configuration de sécurité personnalisé, ou si vous utiliserez le serveur SQL Server en tant qu’un contexte de calcul lors de l’exécution de code R ou Python à partir d’un client distant. 
> 
> Pour plus d’informations, consultez [FAQ d’installation et de mise à niveau](../../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md).
