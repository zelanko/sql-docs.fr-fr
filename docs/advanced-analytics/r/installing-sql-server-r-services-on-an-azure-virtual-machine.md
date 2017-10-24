---
title: Installation de SQL Server R Services sur une machine virtuelle Azure | Microsoft Docs
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e673268b1f6b56890f22576d293135b2675ed4ab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="installing-sql-server-r-services-on-an-azure-virtual-machine"></a>Installation de SQL Server R Services sur une machine virtuelle Azure
 
Si vous déployez une machine virtuelle Azure qui inclut [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez maintenant sélectionner apprentissage en tant que fonctionnalité à ajouter à l’instance de la machine virtuelle est créée.

+ [Create a new VM with SQL Server 2016 and R Services](#new) (Créer une machine virtuelle avec SQL Server 2016 et R Services)
+ [Add R Services to an existing virtual machine with SQL Server 2016](#existing) (Ajouter R Services à une machine virtuelle SQL Server 2016 existante)

## <a name="new"></a>Créer une machine virtuelle SQL Server 2016 Enterprise avec R Services activé

1. Dans le portail Azure, cliquez sur les MACHINES virtuelles et puis cliquez sur Nouveau.
2. Sélectionnez SQL Server 2016 Enterprise Edition.
3. Définissez le nom du serveur et les autorisations de compte, puis sélectionnez un plan tarifaire.
4. À l’étape 4 dans l’Assistant d’installation de la machine virtuelle, dans **Paramètres SQL Server**, recherchez **R Services (Analytique avancée)**, puis cliquez sur **Activer**.
5. Après avoir passé en revue le récapitulatif présenté pour la validation, cliquez sur **OK**.
6. Une fois que la machine virtuelle est prête, connectez-vous à cette machine, puis ouvrez SQL Server Management Studio, qui est préinstallé. R Services est maintenant prêt à être utilisé.
7. Pour le vérifier, ouvrez une nouvelle fenêtre de requête et exécutez une instruction simple, comme celle ci-dessous, qui utilise R pour générer une séquence de nombres de 1 à 10.
   ```
    execute sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
   ```
6. Si vous voulez vous connecter à l’instance à partir d’un client de science des données distant, effectuez les [étapes supplémentaires](#additional-steps) nécessaires.


## <a name="additional-steps"></a>Étapes supplémentaires  

Quelques étapes supplémentaires sont nécessaires si vous pensez que les clients distants d’accéder au serveur en tant qu’un contexte de calcul de SQL Server à distance.

### <a name="firewall"></a>Désactiver une règle du pare-feu

Par défaut, le pare-feu de la machine virtuelle Azure comprend une règle qui bloque l’accès réseau pour les comptes d’utilisateur R locaux.

Vous devez désactiver cette règle pour vous assurer que vous pouvez accéder à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance à partir d’un client de science des données distantes.  Sinon, votre code R ne peut pas s’exécute dans des contextes de calcul qui utilisent l’espace de travail de l’ordinateur virtuel, même si l’autre code R utilise le contexte de calcul de SQL Server sans problème.

Pour autoriser l’accès à R Services à partir des clients de science des données distants :

1. Sur la machine virtuelle, ouvrez le Pare-feu Windows avec fonctions avancées de sécurité.
2. Sélectionnez **Règles sortantes**.
3. Désactivez la règle suivante :
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>Autoriser les rappels ODBC pour les clients distants

Si vous pensez que les clients R qui appellent le serveur auront besoin d’envoyer des requêtes ODBC dans leurs solutions R, vous devez vous assurer que Launchpad peut effectuer des appels ODBC pour le compte du client distant. Pour cela, vous devez autoriser les comptes de travail SQL utilisés par Launchpad à se connecter à l’instance.
Pour plus d’informations, consultez [Configurer SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).

### <a name="network"></a>Ajouter des protocoles réseau

+ Activer les canaux nommés
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilise le protocole des canaux nommés pour les connexions entre les ordinateurs client et serveur, ainsi que pour certaines connexions internes. Si ce protocole n’est pas activé, vous devez l’installer et l’activer sur la machine virtuelle Azure et sur tous les clients de science des données susceptibles de se connecter au serveur.
  
+ Activer TCP/IP

  Vous devez utiliser le protocole TCP/IP pour les connexions de bouclage à SQL Server R Services. Si vous obtenez l’erreur suivante, activez TCP/IP sur l’ordinateur virtuel qui prend en charge de l’instance :

  « DBNETLIB ; SQL Server n’existe pas ou l’accès refusé »

## <a name="how-to-disable-r-services-on-an-instance"></a>Comment désactiver R Services sur une instance

Vous pouvez également activer ou désactiver la fonctionnalité sur une machine virtuelle existante à tout moment.

1. Ouvrez le panneau des machines virtuelles.
2. Cliquez sur **Paramètres**, puis sélectionnez **Configuration de SQL Server**.

## <a name="existing"></a>Ajouter SQL Server R Services à un ordinateur virtuel de SQL Server 2016 Enterprise existant

Si vous avez créé une machine virtuelle Azure qui n’inclut pas de R Services, vous pouvez ajouter la fonctionnalité en suivant ces étapes :

1. Ré-exécutez le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ajoutez la fonctionnalité à partir de la page **Configuration du serveur** de l’Assistant.
2. Activez l’exécution des scripts externes, puis redémarrez l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Configurer SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facultatif) Configurez l’accès aux bases de données pour les comptes de travail R, si cela est nécessaire pour l’exécution des scripts à distance.
   Pour plus d’informations, consultez [Configurer SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md).
3. (Facultatif) Modifiez une règle de pare-feu sur la machine virtuelle Azure, si vous souhaitez autoriser l’exécution de script R à partir des clients de science des données distants. Pour plus d’informations, consultez [Désactiver une règle du pare-feu](#firewall).
4. Installez ou activez les bibliothèques réseau nécessaires. Pour plus d’informations, consultez [Ajouter des protocoles réseau](#network).

## <a name="related-resources"></a>Ressources connexes

[Configurer SQL Server R Services](../../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)

