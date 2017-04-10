---
title: "Installer Microsoft R Server &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "01/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb4446ba-e9ce-4b93-9854-5e8a58507da0
caps.latest.revision: 4
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 3
---
# Installer Microsoft R Server &#224; partir de la ligne de commande
    
Vous pouvez installer Microsoft R Server à partir de la ligne de commande en utilisant les fonctionnalités de création de scripts fournies avec le programme d’installation de SQL Server. 

- Pour une installation **sans assistance**, vous devez spécifier l’emplacement de l’utilitaire d’installation et utiliser des arguments pour indiquer les fonctionnalités à installer. 
- Pour une installation **silencieuse**, fournissez les mêmes arguments et ajoutez le commutateur **/q**. Aucune invite n’est affichée et aucune interaction n’est nécessaire. Toutefois, le programme d’installation échoue si des arguments obligatoires sont omis.

Pour plus d’informations, consultez [Installer SQL Server 2016 à partir de l’invite de commandes](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).

## <a name="perform-a-command-line-install-of-microsoft-r-server-standalone"></a>Effectuer une installation de Microsoft R Server (autonome) à partir de la ligne de commande

 Les exemples suivants montrent les arguments utilisés lors de l’exécution d’une installation à partir de la ligne de commande de Microsoft R Server à l’aide du programme d’installation de SQL Server.


### <a name="example-of-unattended-installation-of-r-server-standalone"></a>Exemple d’installation sans assistance de R Server (autonome)

Exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges pour installer uniquement Microsoft R Server (autonome) et ses composants prérequis. 

```  
Setup.exe /q /ACTION=Install /FEATURES=SQL_SHARED_MR /IACCEPTROPENLICENSETERMS /IACCEPTSQLSERVERLICENSETERMS 
```  

Pour afficher la progression et les invites, supprimez l’argument /q.

Notez que tous les arguments suivants sont obligatoires :
  - **FEATURES = SQL_SHARED_MR** obtient uniquement les composants de Microsoft R Server, notamment Microsoft R Open et les composants prérequis.
  - **IACCEPTROPENLICENSETERMS** indique vous avez accepté les termes du contrat de licence pour l’utilisation des composants open source de R.
  - **IACCEPTSQLSERVERLICENSETERMS** est obligatoire pour exécuter l’Assistant Installation.


### <a name="offline-installation"></a>Installation hors connexion

Si vous installez Microsoft R Server (autonome) sur un ordinateur qui n’a pas accès à Internet, vous devez télécharger au préalable les composants prérequis de R et les copier dans un dossier local. Pour connaître les emplacements de téléchargement, consultez [Installation des composants R sans accès à Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).   


## <a name="advanced-installation-tips"></a>Conseils sur l’installation avancée

Une fois l’installation terminée, vous pouvez consulter le fichier de configuration créé par le programme d’installation de SQL Server, ainsi qu’un résumé des actions d’installation.

Par défaut, l’ensemble des récapitulatifs et journaux du programme d’installation pour SQL Server et les fonctionnalités associées sont créés dans `C:\Program Files\Microsoft SQL Server\140\Setup Bootstrap\Log`.

Un sous-dossier distinct est créé pour chaque fonctionnalité installée. Pour Microsoft R Server, recherchez : 
- `RSetup.log`
- `Settings.xml`
- `Summmary<instance_GUID>.txt`

Pour configurer une autre instance de Microsoft R Server avec les mêmes paramètres, vous pouvez aussi réutiliser le fichier de configuration créé pendant l’installation. Pour plus d’informations, consultez [Installation de SQL Server à l’aide d’un fichier de configuration](https://msdn.microsoft.com/library/dd239405.aspx).



### <a name="customizing-your-r-environment"></a>Personnalisation de votre environnement R

Après l’installation, vous pouvez installer des packages R supplémentaires. Pour plus d’informations, consultez [Installation et gestion des packages R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md).

> [!IMPORTANT]
> Si vous envisagez d’exécuter votre code R sur SQL Server, veillez à installer les mêmes packages sur l’ordinateur client exécutant Microsoft R Server et sur l’instance de SQL Server qui exécute R Services. 



## <a name="see-also"></a>Voir aussi  

[Microsoft R Server](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)
  