---
title: "Installation de SQL Server R Services sur une Machine virtuelle | Microsoft Docs"
ms.custom: ""
ms.date: "12/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c3c223b8-75c4-412e-a319-d57ecf6533af
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Installation de SQL Server R Services sur une Machine virtuelle
 
Si vous déployez une machine virtuelle Azure qui inclut [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez maintenant sélectionner les Services de R en tant que fonctionnalité à ajouter à l’instance lorsque la machine Virtuelle est créée. 



+ [Créer une machine Virtuelle avec SQL Server 2016 et les Services de R](#new)
+ [Ajout de Services de R à une machine virtuelle existante avec SQL Server 2016](#existing)

## <a name="a-namenewacreate-a-new-sql-server-2016-enterprise-virtual-machine-with-r-services-enabled"></a><a name="new"></a>Créer un ordinateur virtuel SQL Server 2016 Enterprise avec R Services activés

1. Dans le portail, cliquez sur MACHINES VIRTUELLES, puis sur NOUVEAU.
2. Sélectionnez SQL Server 2016 Enterprise Edition.
3. Configurer les autorisations de compte et le nom du serveur, puis sélectionnez un plan de tarification.
4. Dans l’étape 4 dans la machine Virtuelle Assistant installation, dans **paramètres SQL Server**, recherchez **Services R (Analytique avancée)** et cliquez sur **Activer**.
5. Lisez le résumé présenté pour la validation et cliquez sur **OK**.
6. Lorsque l’ordinateur virtuel est prêt, s’y connecter et ouvrez SQL Server Management Studio, qui est pré-installé. Services de R est prêt à s’exécuter. 
7. Pour ce faire, vous pouvez ouvrir une nouvelle fenêtre de requête et exécuter une instruction simple comme suit, qui utilise R pour générer une séquence de nombres de 1 à 10.
   ```
    execute sp_execute_external_script
    @language = N'R'
    , @script = N' OutputDataSet <- as.data.frame(seq(1, 10, ));'
    , @input_data_1 = N'   ;'
    WITH RESULT SETS (([Sequence] int NOT NULL));
   ```
6. Si vous doivent se connecter à l’instance à partir d’un client de science des données à distance, exécutez [des étapes supplémentaires](#additional-steps) si nécessaire.


## <a name="additional-steps"></a>Étapes supplémentaires  

Quelques étapes supplémentaires peuvent être nécessaire à l’utilisation de Services de R si vous pensez que les clients distants d’accéder au serveur comme contexte de calcul un serveur SQL distant.

### <a name="a-namefirewallaunblock-the-firewall"></a><a name="firewall"></a>Débloquer le pare-feu  
  
Vous devez modifier une règle de pare-feu sur l’ordinateur virtuel pour vous assurer que vous pouvez accéder à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance à partir d’un client de science des données distantes.  Dans le cas contraire, vous pourrez pas utiliser la clause compute contextes nécessitant utilisent de l’espace de travail de l’ordinateur virtuel. 

Par défaut, le pare-feu sur l’ordinateur virtuel Azure comprend une règle qui bloque réseau d’accès pour les comptes d’utilisateur local R.  
  
Pour activer l’accès aux Services de R à partir de clients de science des données à distance :
1. Sur la machine virtuelle, ouvrez le pare-feu Windows avec fonctions avancées de sécurité.
2. Sélectionnez **règles de trafic sortant**
3. Désactiver la règle suivante :  
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`  
  
### <a name="enable-odbc-callbacks-for-remote-clients"></a>Activer les rappels d’ODBC pour les clients distants

Si vous pensez que les clients R appel du serveur doivent émettre des requêtes ODBC dans le cadre de leurs solutions R, vous devez vous assurer que la zone de lancement peut effectuer des appels ODBC pour le compte du client distant. Pour ce faire, vous devez autoriser les comptes de travail SQL utilisés par Launchpad pour vous connecter à l’instance.
Pour plus d’informations, consultez [configurer SQL Server R le service](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md). 

### <a name="a-namenetworkaadd-network-protocols"></a><a name="network"></a>Ajouter des protocoles réseau  
  
+ Activez les canaux nommés
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilise le protocole canaux nommés pour les connexions entre les ordinateurs client et serveur et pour certaines connexions internes. Si les canaux nommés n’est pas activé, vous devez installer et activer sur la machine virtuelle Azure et sur les clients de science des données qui se connectent au serveur.  
  
+ Activation de TCP/IP

  TCP/IP est requis pour les connexions de bouclage aux Services de R SQL Server. Si vous obtenez l’erreur suivante, activez TCP/IP sur l’ordinateur virtuel qui prend en charge l’instance DBNETLIB ; SQL Server n’existe pas ou l’accès refusé.

## <a name="how-to-disable-r-services-on-an-instance"></a>Comment désactiver les Services de R sur une instance

Vous pouvez également activer ou désactiver la fonctionnalité sur un ordinateur virtuel existant à tout moment. 

1. Ouvrez le panneau de la machine virtuelle
2. Cliquez sur **paramètres**, puis sélectionnez **configuration de SQL Server**.


## <a name="a-nameexistingaadd-sql-server-r-services-to-an-existing-sql-server-2016-enterprise-virtual-machine"></a><a name="existing"></a>Ajouter SQL Server R Services à une machine virtuelle de SQL Server 2016 Enterprise existante

Si vous avez créé une machine Virtuelle Azure avec SQL Server 2016 qui n’inclut pas de Services de R, vous pouvez ajouter la fonctionnalité en procédant comme suit :

1. Exécutez de nouveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le programme d’installation et d’ajouter la fonctionnalité sur le **Configuration du serveur** page de l’Assistant.
2. Activer l’exécution des scripts externes et redémarrez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance. Pour plus d’informations, consultez Voir [configurer SQL Server R le service](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).
3. (Facultatif) Configurer l’accès de base de données pour les comptes de travail R, si nécessaire pour l’exécution de scripts à distance.
   Pour plus d’informations, consultez [configurer SQL Server R le service](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md). 
3. (Facultatif) Modifier une règle de pare-feu sur l’ordinateur virtuel Azure, si vous souhaitez autoriser l’exécution du script R à partir de clients de science des données distantes. Pour plus d’informations, consultez [Débloquer pare-feu](#firewall).
4. Installez ou activez les bibliothèques réseau requises. Pour plus d’informations, consultez [Ajouter des protocoles réseau](#network).

## <a name="see-also"></a>Voir aussi
[Configurer les Services de Sql Server R](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md)