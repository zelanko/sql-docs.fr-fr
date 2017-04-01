---
title: "Configurer et g&#233;rer les extensions analytiques avanc&#233;es | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 20
---
# Configurer et g&#233;rer les extensions analytiques avanc&#233;es
  Après avoir installé [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], vous pouvez apporter des modifications mineures à la configuration du runtime R et d’autres services associés à [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] .  
  
  
 **Dans cette rubrique**  
  
-   [Configuration de comptes d’utilisateur pour SQL Server R Services](#bkmk_Provisioning)  
  
-   [Gestion de l’utilisation de la mémoire par les processus R](#bkmk_ManagingMemory)  
  
-   [Modification des paramètres par défaut du service à l’aide du fichier de configuration](#bkmk_ChangingConfig) 

-   [Modification du compte de Service Launchpad](#bkmk_Launchpad) 
  
##  <a name="bkmk_Provisioning"></a> Configuration de comptes d’utilisateur pour SQL Server R Services  
 R runtime traite dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s’exécutent dans le contexte des comptes d’utilisateur local à faible privilège. L’exécution des processus du runtime R dans des comptes à faible privilège présente les avantages suivants :  
  
-   Ils réduisent les privilèges des processus du runtime R en cours d’exécution sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Assurer l’isolement entre les sessions de runtime R.  
  
 Dans le cadre du processus d’installation dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], une nouvelle fenêtre *pool de compte d’utilisateur* est créé qui contient les comptes d’utilisateur locaux requis pour l’exécution du processus d’exécution R. Vous pouvez modifier le nombre d’utilisateurs si nécessaire pour prendre en charge R. Votre administrateur de base de données doit également autoriser ce groupe pour se connecter à n’importe quelle instance où R Services a été activée. Pour plus d’informations, consultez [Modifier le Pool de compte d’utilisateur pour les Services de SQL Server R](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).  
  
 Toutefois, une liste de contrôle d’accès (ACL) peut être définie pour les ressources sensibles sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour refuser l’accès à ce groupe afin d’empêcher le processus d’exécution R à partir de l’accès aux ressources.  
  
-   Le pool de compte d’utilisateur est lié à une instance spécifique.  Pour chaque instance sur le R le script a été activé, un pool de travail distinct comptes sont créés. Comptes ne peuvent pas être partagés entre des instances.
  
-   Les noms de comptes d’utilisateur dans le pool sont au format SQLInstanceName*nn*. Par exemple, si vous utilisez l’instance par défaut en tant que serveur R, le pool de comptes d’utilisateur prend en charge des noms de compte tels que MSSQLSERVER01, MSSQLSERVER02, et ainsi de suite.  
  
-   La taille du pool de comptes d’utilisateur est statique et sa valeur par défaut est 20. Le nombre de sessions du runtime R qui peuvent s’exécuter simultanément est limité par la taille du pool de ce compte d’utilisateur. Toutefois, cette limite peut être modifiée par un administrateur à l’aide du Gestionnaire de Configuration SQL Server.  
  
  
 Pour plus d’informations sur la modification du pool de comptes d’utilisateur, voir [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).  
  
##  <a name="bkmk_ManagingMemory"></a> Gestion de l’utilisation de la mémoire par les processus R  
 Par défaut, les processus du runtime R associés à [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sont limités à l’utilisation d’au maximum 20 % de la mémoire totale de l’ordinateur. Toutefois, l’administrateur peut augmenter être si nécessaire.  
  
 En règle générale, ce montant sera inadéquat pour des tâches R graves telles que le modèle d’apprentissage ou de prévoir sur plusieurs lignes de données. Vous devrez peut-être réduire la quantité de mémoire réservée pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ou d’autres services) et le gouverneur de ressources permet de définir un pool de ressources externes ou des pools et allouer. Pour plus d’informations, consultez [la gouvernance de ressources pour les Services de R](../../advanced-analytics/r-services/resource-governance-for-r-services.md).  
  
##  <a name="bkmk_ChangingConfig"></a> Modification des Options de Service avancées à l’aide du fichier de Configuration  
 
Vous pouvez contrôler certaines propriétés avancées du [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] en modifiant le [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fichier de configuration. Ce fichier est créé au cours de l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Par défaut, il est enregistré au format de fichier texte brut à l’emplacement suivant :  
 
```  
<instance path>\binn\rlauncher.config  
```  
  
 Pour pouvoir apporter des modifications à ce fichier, vous devez être administrateur sur l’ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous modifiez le fichier, nous vous recommandons de faire une copie de sauvegarde avant d’enregistrer les modifications.  
  
 Par exemple, pour utiliser le Bloc-notes pour ouvrir le fichier de configuration pour l’instance par défaut (MSSQLSERVER), vous serez ouvrir une invite de commandes en tant qu’administrateur, puis taper la commande suivante :  
  
```  
C:\>Notepad.exe "%programfiles%\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\binn\rlauncher.config"  
  
```  
  
###  <a name="bkmk_properties"></a> Propriétés de configuration  
 Tous les paramètres prennent la forme d’une paire clé-valeur, chaque paramètre figurant sur une ligne distincte. Par exemple, cette propriété spécifie que les processus R ne peuvent pas utiliser plus de 20 % de la mémoire système :  
  
 Valeur par défaut : `MEMORY_LIMIT_PERCENT=20`  
  
 Le tableau suivant répertorie chacun des paramètres pris en charge pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], avec les valeurs autorisées.  
  
|Nom du paramètre|Type de valeur|Par défaut|Description|  
|------------------|----------------|-------------|-----------------|  
|JOB_CLEANUP_ON_EXIT|Entier<br /><br /> 0 = Désactivé<br /><br /> 1 = Activé|1<br /><br /> Les fichiers journaux sont supprimés à la sortie|Spécifie si le dossier de travail temporaire créé pour chaque session R doit être nettoyé une fois la session R terminée. Ce paramètre est utile pour le débogage.<br /><br /> Remarque : il s’agit d’un paramètre exclusivement interne ; ne modifiez pas cette valeur.|  
|TRACE_LEVEL|Entier<br /><br /> 1 = Erreur<br /><br /> 2 = les performances<br /><br /> 3 = avertissement<br /><br /> 4 = informations|1<br /><br /> Sortir les avertissements uniquement|Configure le niveau de détail de trace du lanceur R (MSSQLLAUNCHPAD) aux fins de débogage. Ce paramètre affecte le niveau de détail des traces stockées dans les fichiers de trace suivants, tous deux situés dans le chemin d’accès spécifié par le paramètre LOG_DIRECTORY :<br /><br /> **rlauncher.log**: le fichier de trace généré pour les sessions R démarrées par requêtes T-SQL.<br /><br /> Pour plus d'informations sur ce scénario, voir [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md).|  

## <a name="bkmk_Launchpad"></a>Modification du compte de Service Launchpad

Distinct [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] service est créé pour chaque instance sur lequel vous avez configuré [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]. 

Par défaut, le Launchpad est configuré pour s’exécuter avec le compte NT Service\MSSQLLaunchpad, qui est doté de toutes les autorisations nécessaires pour exécuter des scripts R. Toutefois, si vous modifiez ce compte, le Launchpad peut-être pas en mesure de démarrer ou accéder à l’instance de SQL Server dans lequel les scripts R doivent être exécutés.
 
  Si vous modifiez le compte de service, veillez à utiliser le **stratégie de sécurité locale** application et mettre à jour les autorisations sur chaque service de compte afin d’inclure ces autorisations :
  + Changer les quotas de mémoire d'un processus (SeIncreaseQuotaPrivilege)
  + Outrepasser le contrôle de parcours (SeChangeNotifyPrivilege)
  + Ouvrir une session en tant que service (SeServiceLogonRight)
  + Remplacer un jeton de niveau processus (SeAssignPrimaryTokenPrivilege)

Pour plus d’informations sur les autorisations requises pour exécuter les services SQL Server, consultez [configurer des comptes de Service Windows et les autorisations](https://msdn.microsoft.com/library/ms143504.aspx#Windows).
   
## Voir aussi  
 [Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  