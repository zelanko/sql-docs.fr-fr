---
title: "Modifier le pool de comptes d’utilisateurs pour SQL Server R Services | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 33e22f7edec807d046798d89a9cd5daa642e8d3b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="modify-the-user-account-pool-for-sql-server-r-services"></a>Modifier le pool de comptes d’utilisateurs pour SQL Server R Services
  Dans le cadre du processus d’installation de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], un *pool de comptes d’utilisateurs* Windows est créé pour prendre en charge l’exécution de tâches par le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]. L’objectif de ces comptes de travail est d’isoler l’exécution simultanée des scripts R par différents utilisateurs SQL. 

Cette rubrique décrit la configuration par défaut des comptes de travail, leur sécurité et leur capacité, et comment changer la configuration par défaut.

## <a name="worker-accounts-used-by-r-services"></a>Comptes de travail utilisés par R Services   

Le groupe de comptes Windows est créé par l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour chaque instance sur laquelle R Services est installé. Par conséquent, si vous avez installé plusieurs instances qui prennent en charge R, vous aurez plusieurs groupes d’utilisateurs.

-   Dans une instance par défaut, le nom du groupe est **SQLRUserGroup**. 
-   Dans une instance nommée, le nom du groupe par défaut a pour suffixe le nom de l’instance (par exemple, **SQLRUserGroupMyInstanceName**). 

Par défaut, le pool de comptes d’utilisateurs contient 20 comptes d’utilisateurs. Dans la plupart des cas, ce nombre de comptes suffit largement pour prendre en charge les sessions R, mais vous pouvez le revoir à la hausse.
-  Dans une instance par défaut, les comptes individuels sont nommés **MSSQLSERVER01** à **MSSQLSERVER20**.  
-   Pour une instance nommée, les comptes individuels sont nommés en fonction du nom de l’instance (par exemple, **MyInstanceName01** à **MyInstanceName20**).  

### <a name = "HowToChangeGroup"> </a>Comment changer le nombre de comptes de travail R

Pour modifier le nombre d’utilisateurs dans le pool de comptes, vous devez modifier les propriétés du service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], comme décrit ci-dessous.  
  
Les mots de passe associés à chaque compte d’utilisateur sont générés de manière aléatoire, mais vous pouvez les modifier une fois les comptes créés.  
  
1. Ouvrez le Gestionnaire de configuration SQL Server, puis sélectionnez **SQL Server Services**.
2. Double-cliquez sur le service SQL Server Launchpad et arrêtez-le s’il est en cours d’exécution. 
3.  Sous l’onglet **Service**, vérifiez que le mode de démarrage Automatique est sélectionné. Le script R échoue si Launchpad n’est pas en cours d’exécution.
4.  Cliquez sur l’onglet **Avancé** et, si nécessaire, modifiez le **Nombre d’utilisateurs externes**. Ce paramètre contrôle le nombre d’utilisateurs SQL pouvant exécuter simultanément des requêtes dans R. La valeur par défaut est de 20 comptes.
5. Vous pouvez éventuellement affecter à l’option **Réinitialiser le mot de passe des utilisateurs externes** la valeur _Oui_ si une stratégie exigeant le changement périodique des mots de passe est en place dans votre organisation. Cette opération regénère les mots de passe chiffrés que gère Launchpad pour les comptes d’utilisateurs. Pour plus d’informations, consultez [Appliquer la stratégie des mots de passe](#bkmk_EnforcePolicy).    
6.  Redémarrage du service.  

## <a name="managing-r-workload"></a>Gestion de la charge de travail R

Le nombre de comptes figurant dans ce pool détermine le nombre de session R qui peuvent être actives simultanément.  Par défaut, 20 comptes sont créés, ce qui signifie que 20 utilisateurs peuvent avoir des sessions R actives à un moment donné. Si vous prévoyez une augmentation du nombre d’utilisateurs devant exécuter simultanément des scripts R, vous pouvez revoir le nombre de comptes de travail à la hausse. 

Quand le même utilisateur exécute simultanément plusieurs scripts R, toutes les sessions exécutées par l’utilisateur utilisent le même compte de travail. Par exemple, un utilisateur unique peut exécuter simultanément 100 scripts R différents, dans la limite des ressources, avec un seul compte de travail.

Les ressources du serveur sont les seules à limiter le nombre de comptes de travail que vous pouvez prendre en charge et le nombre de sessions R simultanées qu’un utilisateur peut exécuter.  En général, la mémoire est le premier goulot d’étranglement que vous rencontrez quand vous utilisez le runtime R.

Dans R Services, les ressources qui peuvent être utilisées par les scripts R sont régies par SQL Server. Nous vous recommandons de surveiller l’utilisation des ressources à l’aide de vues de gestion dynamique de SQL Server, ou d’examiner les compteurs de performances sur l’objet de traitement Windows associé, puis d’ajuster l’utilisation de la mémoire du serveur en conséquence. 
 
Si vous avez SQL Server Enterprise Edition, vous pouvez allouer les ressources utilisées pour l’exécution de scripts R en configurant un [pool de ressources externes](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md). 

Pour plus d’informations sur la gestion de la capacité des scripts R, consultez les articles suivants :

- [Configuration de SQL Server (R Services)](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
-  [Étude de cas sur les performances (R Services)](../../advanced-analytics/r-services/performance-case-study-r-services.md)

## <a name="security"></a>Sécurité

Chaque groupe d’utilisateurs est associé au service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] sur une instance spécifique et ne peut pas prendre en charge les travaux R qui s’exécutent sur d’autres instances.

Pour chaque compte de travail, quand la session est active, un dossier temporaire est créé pour stocker les objets de script, les résultats intermédiaires et d’autres informations utilisées par R et SQL Server pendant l’exécution du script R. Ces fichiers de travail, situés sous le dossier ExtensibilityData, sont uniquement accessibles aux administrateurs et sont nettoyés par SQL Server une fois le script terminé. 

Pour plus d’informations, consultez [Vue d’ensemble de la sécurité](../../advanced-analytics/r-services/security-overview-sql-server-r.md).

### <a name="bkmk_EnforcePolicy"></a>Application de la stratégie de mot de passe

Si votre organisation a mis en place une stratégie exigeant le changement périodique des mots de passe, vous devrez peut-être forcer le service Launchpad à regénérer les mots de passe chiffrés qu’il gère pour ses comptes de travail.  

Pour activer ce paramètre et forcer l’actualisation des mots de passe, ouvrez le volet **Propriétés** du service Launchpad dans le Gestionnaire de configuration SQL Server, cliquez sur **Avancé**, puis affectez à **Réinitialiser le mot de passe des utilisateurs externes** la valeur **Oui**. Quand vous appliquez ce changement, les mots de passe sont immédiatement regénérés pour tous les comptes d’utilisateurs. Pour utiliser le script R après ce changement, vous devez redémarrer le service Launchpad. À ce stade, les mots de passe qui viennent d’être générés sont lus. 

Pour réinitialiser les mots de passe à intervalles réguliers, vous pouvez définir cet indicateur manuellement ou utiliser un script.

### <a name="additional-permission-required-to-support-remote-compute-contexts"></a>Autres autorisations nécessaires pour prendre en charge les contextes de calcul à distance

Par défaut, le groupe de comptes de travail R **ne dispose pas** d’autorisations de connexion sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle il est associé. Cela peut poser problème si des utilisateurs R se connectent à SQL Server à partir d’un client distant pour exécuter des scripts R, ou si un script utilise ODBC pour obtenir des données supplémentaires. 

Pour vérifier que ces scénarios sont pris en charge, l’administrateur de base de données doit accorder au groupe de comptes de travail R l’autorisation de se connecter à l’instance de SQL Server sur laquelle le script R sera exécuté (autorisations **Se connecter à**). Cette approche, appelée *authentification implicite*, permet à SQL Server d’exécuter les scripts R en utilisant les informations d’identification de l’utilisateur distant.

> [!NOTE]
> Cette limitation ne s’applique pas si vous utilisez des connexions SQL pour exécuter des scripts R à partir d’une station de travail distante, car les informations d’identification de connexion SQL sont transmises explicitement du client R vers l’instance SQL Server, puis vers ODBC.


### <a name="how-to-enable-implied-authentication"></a>Comment activer l’authentification implicite

1. Ouvrez SQL Server Management Studio comme administrateur sur l’instance sur laquelle vous allez exécuter le code R.

2. Exécutez le script suivant. Veillez à modifier le nom du groupe d’utilisateurs, si vous avez modifié la valeur par défaut, ainsi que le nom de l’ordinateur et de l’instance.

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\SQLRUserGroup] FROM WINDOWS WITH DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO  
    ````


  
## <a name="see-also"></a>Voir aussi  
 [Configuration (SQL Server R Services)](../../advanced-analytics/r-services/configuration-sql-server-r-services.md)
  

