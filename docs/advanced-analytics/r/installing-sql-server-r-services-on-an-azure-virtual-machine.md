---
title: "L’installation des fonctionnalités de formation l’ordinateur SQL Server sur une machine virtuelle Azure | Documents Microsoft"
ms.custom: 
ms.date: 10/31/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: "11"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 0c4b8ef73f4afbc54d2fc1841e281afd0342cedf
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-sql-server-machine-learning-features-on-an-azure-virtual-machine"></a>L’installation de fonctionnalités sur une machine virtuelle Azure d’apprentissage automatique SQL Server
 
Si vous déployez une machine virtuelle Azure qui inclut [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez maintenant sélectionner apprentissage en tant que fonctionnalité à ajouter à l’instance de la machine virtuelle est créée.

+ [Créer une machine virtuelle qui inclut SQL Server 2016 et R Services](#new)
+ [Ajouter des fonctionnalités de machine learning à une machine virtuelle existante avec SQL Server 2016](#existing)

> [!NOTE]
> Machines virtuelles sont désormais disponibles pour SQL Server 2017 ! Consultez [cette annonce](https://azure.microsoft.com/blog/announcing-new-azure-vm-images-sql-server-2017-on-linux-and-windows/) pour plus d’informations.
> 
> R est également disponible sous une fonctionnalité d’aperçu dans la base de données SQL Azure. Pour plus d’informations, consultez [à l’aide de R dans Azure SQL Database](../r/using-r-in-azure-sql-database.md).

## <a name="create-a-new-sql-server-2017-virtual-machine"></a>Créer un ordinateur virtuel SQL Server 2017

Pour utiliser R ou Python dans SQL Server 2017, veillez à obtenir un ordinateur virtuel basé sur Windows. [!INCLUDE[sscurrentlong-md](../../includes/sscurrentlong-md.md)]sur Linux prend en charge fast [score native](../sql-native-scoring.md) à l’aide de la fonction de prédiction de T-SQL, mais d’autres fonctionnalités d’apprentissage n’existe pas encore dans cette édition.

Pour obtenir la liste des offres de machine virtuelle SQL Server, consultez l’article : [vue d’ensemble de SQL Server sur des Machines virtuelles Azure (Windows)](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-server-iaas-overview).

### <a name="new"></a>Créer une nouvelle machine virtuelle SQL Server Enterprise avec machine learning

1. Dans le portail Azure, cliquez sur les MACHINES virtuelles et puis cliquez sur Nouveau.
2. Sélectionnez SQL Server 2017 Enterprise Edition.
3. Définissez le nom du serveur et les autorisations de compte, puis sélectionnez un plan tarifaire.
4. Dans **paramètres SQL Server** (étape 4 de l’Assistant Installation de machine virtuelle), recherchez **Machine Learning Services (Analytique avancée)** et cliquez sur **activer**.
5. Après avoir passé en revue le récapitulatif présenté pour la validation, cliquez sur **OK**.
6. Une fois que la machine virtuelle est prête, connectez-vous à cette machine, puis ouvrez SQL Server Management Studio, qui est préinstallé. Machine learning n’est prêt à s’exécuter.
7. Pour le vérifier, ouvrez une nouvelle fenêtre de requête et exécutez une instruction simple, comme celle ci-dessous, qui utilise R pour générer une séquence de nombres de 1 à 10.

    ```
    EXEC sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
    ```

6. Si vous envisagez de vous connecter à l’instance à partir d’un client de science des données à distance, effectuez [des étapes supplémentaires](#additional-steps) si nécessaire.

### <a name="disable-machine-learning-features-on-a-sql-server-vm"></a>Désactiver les fonctionnalités d’apprentissage machine sur une machine virtuelle SQL Server

Vous pouvez également activer ou désactiver la fonctionnalité sur un ordinateur virtuel de SQL Server existant à tout moment.

1. Ouvrez le panneau de l’ordinateur virtuel.
2. Cliquez sur **Paramètres**, puis sélectionnez **Configuration de SQL Server**.
3. Apporter des modifications aux fonctionnalités et s’appliquent.

### <a name="existing"></a>Ajouter R Services à un SQL Server 2016 Enterprise machine virtuelle existante

Si vous avez créé une machine virtuelle Azure incluant SQL Server sans l’apprentissage automatique, vous pouvez ajouter la fonctionnalité en suivant ces étapes :

1. Ré-exécutez le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ajoutez la fonctionnalité à partir de la page **Configuration du serveur** de l’Assistant.
2. Activez l’exécution des scripts externes, puis redémarrez l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [configurer SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facultatif) Configurez l’accès aux bases de données pour les comptes de travail R, si cela est nécessaire pour l’exécution des scripts à distance.
   Pour plus d’informations, consultez [Configurer SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facultatif) Modifiez une règle de pare-feu sur la machine virtuelle Azure, si vous souhaitez autoriser l’exécution de script R à partir des clients de science des données distants. Pour plus d’informations, consultez [Désactiver une règle du pare-feu](#firewall).
4. Installez ou activez les bibliothèques réseau nécessaires. Pour plus d’informations, consultez [Ajouter des protocoles réseau](#network).

## <a name="additional-steps"></a>Étapes supplémentaires

Quelques étapes supplémentaires sont nécessaires si vous pensez que les clients distants d’accéder au serveur en tant qu’un contexte de calcul de SQL Server à distance.

### <a name="firewall"></a>Désactiver une règle du pare-feu

Par défaut, le pare-feu sur l’ordinateur virtuel Azure comprend une règle qui bloque accès pour les comptes d’utilisateurs locaux l'réseau.

Vous devez désactiver cette règle pour vous assurer que vous pouvez accéder à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance à partir d’un client de science des données distantes.  Sinon, votre code d’apprentissage ne peut pas s’exécute dans des contextes de calcul qui utilisent l’espace de travail de l’ordinateur virtuel.

Pour activer l’accès à partir de clients de science des données à distance :

1. Sur la machine virtuelle, ouvrez le Pare-feu Windows avec fonctions avancées de sécurité.
2. Sélectionnez **Règles sortantes**.
3. Désactivez la règle suivante :
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>Autoriser les rappels ODBC pour les clients distants

Si vous prévoyez que les clients de l’appel du serveur doivent émettre des requêtes ODBC dans le cadre de leur solutions d’apprentissage, vous devez vous assurer que le Launchpad peut effectuer des appels ODBC part du client distant. Pour cela, vous devez autoriser les comptes de travail SQL utilisés par Launchpad à se connecter à l’instance.
Pour plus d’informations, consultez [Configurer SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).

### <a name="network"></a>Ajouter des protocoles réseau

+ Activer les canaux nommés
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilise le protocole des canaux nommés pour les connexions entre les ordinateurs client et serveur, ainsi que pour certaines connexions internes. Si ce protocole n’est pas activé, vous devez l’installer et l’activer sur la machine virtuelle Azure et sur tous les clients de science des données susceptibles de se connecter au serveur.
  
+ Activer TCP/IP

  TCP/IP est requis pour les connexions de bouclage. Si vous obtenez l’erreur suivante, activez TCP/IP sur l’ordinateur virtuel qui prend en charge de l’instance :

  « DBNETLIB ; SQL Server n’existe pas ou l’accès refusé »

## <a name="related-resources"></a>Ressources connexes

[À l’aide de R dans la base de données SQL Azure](../r/using-r-in-azure-sql-database.md)