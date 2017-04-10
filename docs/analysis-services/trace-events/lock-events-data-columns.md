---
title: "Colonnes de donn&#233;es des &#233;v&#233;nements de verrou | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c223157f-41a0-405c-bc1a-41c999506936
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# Colonnes de donn&#233;es des &#233;v&#233;nements de verrou
  La catégorie d'événements Verrous contient les classes d'événements suivantes :  
  
|**ID d'événement**|**Nom d'événement**|**Description de l'événement**|  
|------------------|--------------------|---------------------------|  
|50|Deadlock|Informations sur les verrous actifs dans l'état de blocage.|  
|51|Lock Timeout|Informations sur les verrous qui ont expiré récemment|  
|52|Lock Acquired|Informations sur les verrous récemment acquis|  
|53|Lock Released|Informations sur les verrous récemment libérés|  
|54|Lock Waiting|Informations sur les verrous en attente sur d'autres verrous|  
  
 Le tableau suivant répertorie les colonnes de données de cette classe d'événements.  
  
## Deadlock  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Classe d'événements utilisée pour catégoriser les événements.|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|DatabaseName|28|8|Nom de la base de données dans laquelle l'instruction de l'utilisateur s'exécute.|  
|TextData|42|9|Données texte associées à l'événement.|  
|ServerName|43|8|Nom du serveur produisant l'événement.|  
  
## Lock Timeout  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Classe d'événements utilisée pour catégoriser les événements.|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|StartTime|3|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|EndTime|4|5|Heure de fin de l'événement. Cette colonne n'est pas remplie pour les classes d'événements de démarrage, comme SQL:BatchStarting ou SP:Starting. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|Duration|5|2|Durée (en millisecondes) de l'événement.|  
|IntegerData|10|1|Données de type Integer (entier).|  
|ObjectType|12|1|Type d'objet.|  
|ObjectPath|14|8|Chemin d'accès de l'objet. Liste de parents séparés par une virgule, commençant par le parent de l'objet.|  
|ConnectionID|25|1|ID de connexion unique.|  
|DatabaseName|28|8|Nom de la base de données dans laquelle l'instruction de l'utilisateur s'exécute.|  
|NTUserName|32|8|Nom d'utilisateur Windows.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|SessionID|39|8|GUID de session.|  
|NTCanonicalUserName|40|8|Nom d'utilisateur sous forme canonique. Par exemple, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID de processus serveur. Cela identifie de façon unique une session utilisateur. Le SPID correspond directement au GUID de session utilisé par XML/A.|  
|ServerName|43|8|Nom du serveur produisant l'événement.|  
  
## Lock Acquired  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Classe d'événements utilisée pour catégoriser les événements.|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|ConnectionID|25|1|ID de connexion unique.|  
|NTUserName|32|8|Nom d'utilisateur Windows.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|ClientHostName|35|8|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.|  
|ClientProcessID|36|1|ID de processus de l'application cliente.|  
|ApplicationName|37|8|Nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SessionID|39|8|GUID de session.|  
|NTCanonicalUserName|40|8|Nom d'utilisateur sous forme canonique. Par exemple, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID de processus serveur. Cela identifie de façon unique une session utilisateur. Le SPID correspond directement au GUID de session utilisé par XML/A.|  
|TextData|42|9|Données texte associées à l'événement.|  
|ServerName|43|8|Nom du serveur produisant l'événement.|  
  
## Lock Released  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Classe d'événements utilisée pour catégoriser les événements.|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|ConnectionID|25|1|ID de connexion unique.|  
|NTUserName|32|8|Nom d'utilisateur Windows.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|ClientHostName|35|8|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.|  
|ClientProcessID|36|1|ID de processus de l'application cliente.|  
|ApplicationName|37|8|Nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SessionID|39|8|GUID de session.|  
|NTCanonicalUserName|40|8|Nom d'utilisateur sous forme canonique. Par exemple, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID de processus serveur. Cela identifie de façon unique une session utilisateur. Le SPID correspond directement au GUID de session utilisé par XML/A.|  
|TextData|42|9|Données texte associées à l'événement.|  
|ServerName|43|8|Nom du serveur produisant l'événement.|  
  
## Lock Waiting  
  
|**Nom de la colonne**|**ID de la colonne**|**Type de colonne**|**Description de la colonne**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|Classe d'événements utilisée pour catégoriser les événements.|  
|CurrentTime|2|5|Heure à laquelle a débuté l'événement, si disponible. Pour le filtrage, les formats attendus sont « YYYY-MM-DD » et « YYYY-MM-DD HH:MM:SS ».|  
|ConnectionID|25|1|ID de connexion unique.|  
|NTUserName|32|8|Nom d'utilisateur Windows.|  
|NTDomainName|33|8|Domaine Windows auquel appartient l'utilisateur.|  
|ClientHostName|35|8|Nom de l'ordinateur sur lequel le client est exécuté. Cette colonne de données est remplie si le nom de l'hôte est fourni par le client.|  
|ClientProcessID|36|1|ID de processus de l'application cliente.|  
|ApplicationName|37|8|Nom de l'application cliente qui a créé la connexion au serveur. Cette colonne est remplie avec les valeurs passées par l'application plutôt que par le nom affiché du programme.|  
|SessionID|39|8|GUID de session.|  
|NTCanonicalUserName|40|8|Nom d'utilisateur sous forme canonique. Par exemple, engineering.microsoft.com/software/someone.|  
|SPID|41|1|ID de processus serveur. Cela identifie de façon unique une session utilisateur. Le SPID correspond directement au GUID de session utilisé par XML/A.|  
|TextData|42|9|Données texte associées à l'événement.|  
|ServerName|43|8|Nom du serveur produisant l'événement.|  
  
## Voir aussi  
 [Catégorie d'événements de verrou](../../analysis-services/trace-events/lock-events-category.md)  
  
  