---
title: Utilitaire sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 11/29/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- statements [SQL Server], command prompt
- QUIT command
- Transact-SQL statements, command prompt
- EXIT command
- sqlcmd commands
- ED command
- sqlcmd utility
- command prompt utilities [SQL Server], sqlcmd
- '!! command'
- stored procedures [SQL Server], command prompt
- system stored procedures [SQL Server], command prompt
- sqlcmd utility, about sqlcmd utility
- scripts [SQL Server], command prompt
- RESET command
- GO command
ms.assetid: e1728707-5215-4c04-8320-e36f161b834a
caps.latest.revision: 115
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 04edfd00a4f298e944837153e5e71f3c832a17f2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303439"
---
# <a name="sqlcmd-utility"></a>sqlcmd Utility
  Le `sqlcmd` utilitaire vous permet d’entrer [!INCLUDE[tsql](../includes/tsql-md.md)] script, instructions et procédures système de fichiers à l’invite de commandes, dans **éditeur de requête** en mode SQLCMD, dans un fichier de script Windows ou dans une étape de travail de système d’exploitation (Cmd.exe) d’un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Travail de l’agent. Cet utilitaire utilise ODBC pour exécuter des traitements [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] utilise le [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]SqlClient pour l’exécution en Normal et le mode SQLCMD dans **éditeur de requête**. Lorsque `sqlcmd` est exécuté à partir de la ligne de commande `sqlcmd` utilise le pilote ODBC. Dans la mesure où différentes options par défaut peuvent s'appliquer, vous pouvez constater un comportement différent lorsque vous exécutez la même requête dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] en mode SQLCMD et dans l'utilitaire `sqlcmd`.  
  
 Actuellement, `sqlcmd` ne requiert pas d'espace entre l'option de ligne de commande et la valeur. Toutefois, dans une version ultérieure, un espace peut être requis entre l'option de ligne de commande et la valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   sqlcmd  
   -a  
   packet_size  
   -A (dedicated administrator connection)  
-b (terminate batch job if there is an error)  
-cbatch_terminator-C (trust the server certificate)  
-ddb_name-e (echo input)  
-E (use trusted connection)  
-fcodepage | i:codepage[,o:codepage] | o:codepage[,i:codepage]  
-hrows_per_header-Hworkstation_name-iinput_file-I (enable quoted identifiers)  
-k[1 | 2] (remove or replace control characters)  
-Kapplication_intent-llogin_timeout-L[c] (list servers, optional clean output)  
-merror_level-Mmultisubnet_failover-N (encrypt connection)  
-ooutput_file-p[1] (print statistics, optional colon format)  
-Ppassword-q "cmdline query"-Q "cmdline query" (and exit)  
-r[0 | 1] (msgs to stderr)  
-R (use client regional settings)  
-scol_separator-S [protocol:]server[\instance_name][,port]  
-tquery_timeout-u (unicode output file)  
-Ulogin_id-vvar = "value"-Verror_severity_level-wcolumn_width-W (remove trailing spaces)  
-x (disable variable substitution)  
-X[1] (disable commands, startup script, environment variables and optional exit)  
-yvariable_length_type_display_width-Yfixed_length_type_display_width-znew_password -Znew_password (and exit)  
  
-? (usage)  
```  
  
## <a name="command-line-options"></a>Options de ligne de commande  
 **Options relatives à la connexion**  
  **-A**  
 Se connecte à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec une connexion administrateur dédiée (Dedicated Administrator Connection). Ce type de connexion est utilisé pour dépanner un serveur. Elle ne fonctionne qu'avec les serveurs prenant en charge DAC. Si DAC n'est pas disponible, `sqlcmd` génère un message d'erreur et se termine. Pour plus d’informations sur DAC, consultez [Connexion de diagnostic pour les administrateurs de base de données](../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).  
  
 **-C**  
 Ce commutateur est utilisé par le client pour le configurer afin d'approuver implicitement le certificat de serveur sans validation. Cette option est équivalente à l'option ADO.NET `TRUSTSERVERCERTIFICATE = true`.  
  
 **-d** *nom_base_de_données*  
 Problèmes un `USE` *db_name* instruction lorsque vous démarrez `sqlcmd`. Cette option définit la variable de script `sqlcmd` SQLCMDDBNAME. Celle-ci spécifie la base de données initiale. La valeur par défaut est la propriété de base de données par défaut de votre connexion. Si la base de données n'existe pas, un message d'erreur est généré et `sqlcmd` se termine.  
  
 **-l** *délai_d’attente_connexion*  
 Spécifie le nombre de secondes au terme duquel une connexion `sqlcmd` au pilote ODBC expire lorsque vous tentez d'établir une connexion à un serveur. Cette option définit la variable de script `sqlcmd` SQLCMDLOGINTIMEOUT. Le délai d'attente par défaut pour la connexion à `sqlcmd` est de huit secondes. Le délai d'attente de la connexion doit être un nombre compris entre 0 et 65534. Si la valeur fournie n'est pas numérique ou n'est pas comprise dans cet intervalle, `sqlcmd` génère un message d'erreur. Une valeur de 0 spécifie un délai d'attente infini.  
  
 **-E**  
 Utilise une connexion approuvée au lieu d'un nom d'utilisateur et un mot de passe pour vous connecter à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Par défaut, lorsque -E est spécifié, `sqlcmd` utilise l'option de connexion approuvée.  
  
 L’option **-E** ignore les éventuels paramètres de variables d’environnement de nom d’utilisateur et de mot de passe, tels que SQLCMDPASSWORD. Si l’option **-E** est utilisée avec l’option **-U** ou **-P**, un message d’erreur est généré.  
  
 **-H** *nom_de_la_station_de_travail*  
 Nom d'une station de travail. Cette option définit la variable de script `sqlcmd` SLCMDWORKSTATION. Le nom de la station de travail est indiqué dans la colonne **hostname**de l’affichage catalogue **sys.processes** et peut être retourné à l’aide de la procédure stockée **sp_who**. Si cette option n'est pas spécifiée, le nom de l'ordinateur actif est utilisé par défaut. Ce nom peut être utilisé pour identifier différentes sessions `sqlcmd`.  
  
 **-K** *application_intent*  
 Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. La seule valeur actuellement prise en charge est **ReadOnly**. Si **-K** n’est pas spécifié, l’utilitaire sqlcmd ne prend pas en charge la connectivité à un réplica secondaire dans un groupe de disponibilité AlwaysOn. Pour plus d’informations, consultez [secondaires actifs : réplicas secondaires lisibles](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 `-M` *multisubnet_failover*  
 Spécifiez toujours `-M` lors de la connexion à l’écouteur de groupe de disponibilité d’un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] groupe de disponibilité ou un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instance de Cluster de basculement. `-M` fournit une détection plus rapide du serveur actif et une connexion à celui-ci. Si `–M` n'est pas spécifié, `-M` est désactivé. Pour plus d’informations sur [!INCLUDE[ssHADR](../includes/sshadr-md.md)], consultez [écouteurs de groupe de disponibilité, connectivité Client et basculement d’Application &#40;SQL Server&#41;](../database-engine/listeners-client-connectivity-application-failover.md), [la création et Configuration des groupes de disponibilité &#40;SQL Server&#41;](../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md), [Clustering de basculement et groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md), et [secondaires actifs : réplicas secondaires lisibles ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) .  
  
 **-N**  
 Ce commutateur est utilisé par le client pour demander une connexion chiffrée.  
  
 **-P** *password*  
 Spécifie le mot de passe pour l'utilisateur. Les mots de passe respectent la casse. Si l’option-u est utilisée et la **-P** option n’est pas utilisée, et la variable d’environnement SQLCMDPASSWORD n’a pas été définie, `sqlcmd` invite l’utilisateur à un mot de passe. Si le **-P** option est utilisée à la fin de l’invite de commandes sans mot de passe `sqlcmd` utilise le mot de passe par défaut (NULL).  
  
> [!IMPORTANT]  
>  N'utilisez pas de mot de passe vide. Utilisez un mot de passe fort. Pour plus d’informations, consultez [Strong Passwords](../relational-databases/security/strong-passwords.md).  
  
 L’invite de mot de passe s’affiche en imprimant l’invite de commande sur la console, comme suit : `Password:`  
  
 L'entrée de l'utilisateur est masquée, ce qui signifie que rien ne s'affiche et que le curseur reste immobile.  
  
 La variable d'environnement SQLCMDPASSWORD vous permet de définir un mot de passe par défaut pour la session en cours. Par conséquent, les mots de passe n'ont pas besoin d'être codés en dur dans des fichiers de commandes.  
  
 L'exemple suivant définit la variable SQLCMDPASSWORD au niveau de l'invite de commandes et accède ensuite à l'utilitaire `sqlcmd`. À l'invite de commandes, tapez :  
  
 `SET SQLCMDPASSWORD= p@a$$w0rd`  
  
> [!IMPORTANT]  
>  Le mot de passe sera visible par toute personne pouvant voir l'écran de l'ordinateur.  
  
 À l'invite de commandes suivante, tapez :  
  
 `sqlcmd`  
  
 Si la combinaison de nom d'utilisateur et de mot de passe est incorrecte, un message d'erreur est généré.  
  
> [!NOTE]  
>  La variable d'environnement OSQLPASSWORD a été conservée pour garantir une compatibilité descendante. La variable d’environnement SQLCMDPASSWORD est prioritaire sur la variable d’environnement OSQLPASSWORD ; Cela signifie que `sqlcmd` et **osql** peuvent être utilisés côté à l’autre sans interférence et les anciens scripts continuent à fonctionner.  
  
 Si l’option **-P** est utilisée avec l’option **-E** , un message d’erreur est généré.  
  
 Si l’option **-P** est suivie de plusieurs arguments, un message d’erreur est généré et le programme se termine.  
  
 **S -** [*protocole*:]*server*[**\\***nom_instance*] [**, ***port*]  
 Spécifie l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à laquelle établir une connexion. Cette option définit la variable de script `sqlcmd` SQLCMDSERVER.  
  
 Spécifiez *nom_serveur* pour vous connecter à l’instance par défaut du [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur cet ordinateur serveur. Spécifiez *nom_serveur* [**\\*** nom_instance* ] pour vous connecter à une instance nommée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur ce serveur. Si aucun ordinateur serveur n'est spécifié, l'utilitaire `sqlcmd` se connecte à l'instance par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l'ordinateur local. Cette option est indispensable lorsque vous exécutez `sqlcmd` à partir d’un ordinateur distant sur le réseau.  
  
 *protocole* peut être `tcp` (TCP/IP), `lpc` (mémoire partagée), ou `np` (canaux nommés).  
  
 Si vous ne spécifiez pas un *nom_serveur* [**\\*** nom_instance* ] lorsque vous démarrez `sqlcmd`, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] recherche et utilise la variable d’environnement SQLCMDSERVER.  
  
> [!NOTE]  
>  La variable d'environnement OSQLSERVER a été conservée pour assurer une compatibilité descendante. La variable d’environnement SQLCMDSERVER est prioritaire sur la variable d’environnement OSQLSERVER ; Cela signifie que `sqlcmd` et **osql** peuvent être utilisés côté à l’autre sans interférence et les anciens scripts continuent à fonctionner.  
  
 **-U** *ID_connexion*  
 ID de connexion de l'utilisateur.  
  
> [!NOTE]  
>  La variable d'environnement OSQLUSER est disponible à des fins de compatibilité descendante. La variable d'environnement SQLCMDUSER est prioritaire par rapport à la variable d'environnement OSQLUSER. Cela signifie que `sqlcmd` et **osql** peut être utilisé en regard de l’autre sans interférence. Cela signifie également que les scripts **osql** existants continueront de fonctionner.  
  
 Si ni le **- U** option ni le **-P** option est spécifiée, `sqlcmd` tente de se connecter à l’aide de [!INCLUDE[msCoName](../includes/msconame-md.md)] mode d’authentification Windows. L'authentification est basée sur le compte Windows de l'utilisateur exécutant `sqlcmd`.  
  
 Si l’option **-U** est utilisée avec l’option **-E** (décrite plus loin dans cette rubrique), un message d’erreur est généré. Si l’option **–U** est suivie de plusieurs arguments, un message d’erreur est généré et le programme se termine.  
  
 **-z** *nouveau_mot_de_passe*  
 Modifier le mot de passe :  
  
 `sqlcmd -U someuser -P s0mep@ssword -z a_new_p@a$$w0rd`  
  
 **-Z** *nouveau_mot_de_passe*  
 Modifier le mot de passe et quitter :  
  
 `sqlcmd -U someuser -P s0mep@ssword -Z a_new_p@a$$w0rd`  
  
 **Options d’entrée/sortie**  
  **-f** *codepage* | **i:***codepage*[**,o:***codepage*] | **o:***codepage*[**,i:*** codepage*]  
 Spécifie les pages de codes d'entrée et de sortie. Le numéro de pages de codes est une valeur numérique spécifiant une page de codes Windows installée.  
  
 Règles de conversion des pages de code :  
  
-   Si aucune page de codes n'est spécifiée, `sqlcmd` utilise la page de codes en cours, à la fois pour le fichier d'entrée et le fichier de sortie, sauf si le fichier d'entrée est un fichier Unicode, auquel cas aucune conversion n'est requise.  
  
-   `sqlcmd` reconnaît automatiquement les fichiers d'entrée Unicode Big-endian et Little-endian. Si l’option **-u** est spécifiée, les données de sortie sont toujours de type Unicode Little-endian.  
  
-   Si aucun fichier de sortie n'est spécifié, la page de codes de sortie correspond à la page de codes de la console. Cela permet aux données de sortie d'être correctement affichées sur la console.  
  
-   Plusieurs fichiers d'entrée sont supposés correspondre à une même page de codes. Les fichiers d'entrée Unicode et non Unicode peuvent être mélangés.  
  
 Entrez `chcp` à l’invite de commandes pour vérifier la page de codes de Cmd.exe.  
  
 **i -** *input_file*[**, *** input_file2*...]  
 Identifie le fichier contenant un traitement d'instructions SQL ou des procédures stockées. Plusieurs fichiers peuvent être spécifiés, ils sont lus et traités dans l'ordre. N'utilisez pas d'espace entre les noms de fichiers. `sqlcmd` vérifie d'abord que tous les fichiers spécifiés existent. Si un ou plusieurs fichiers n'existent pas, `sqlcmd` se termine. Les options -i et -Q/-q s'excluent mutuellement.  
  
 Exemples de chemins :  
  
 **i -** C:\\< nom de fichier\>  
  
 **i -** \\ \\< Server\>\\< partage$ >\\< nom de fichier\>  
  
 **-i** "C:\Dossier\\<nom_fichier\>"  
  
 Les chemins d'accès aux fichiers comportant des espaces doivent être placés entre guillemets.  
  
 Cette option peut être utilisée plusieurs fois : **-i***input_file* **-I***I input_file.*  
  
 **-o** *output_file*  
 Identifie le fichier recevant une sortie de `sqlcmd`.  
  
 Si **-u** est spécifié, le *fichier_sortie* est stocké au format Unicode. Si le nom de fichier n'est pas valide, un message d'erreur est généré et `sqlcmd` se termine. `sqlcmd` ne prend pas en charge l'écriture simultanée de plusieurs processus `sqlcmd` dans le même fichier. La sortie fichier sera endommagée ou incorrecte. Pour plus d’informations sur les formats de fichier, consultez le commutateur **-f** . Ce fichier sera créé s'il n'existe pas. Un fichier portant le même nom qui provient d'une session `sqlcmd` antérieure sera remplacé. Le fichier spécifié ici n'est pas le fichier **stdout** . Si un fichier **stdout** est spécifié, ce fichier ne sera pas utilisé.  
  
 Exemples de chemins :  
  
 **-o** C:\\<nom_fichier>  
  
 **-o** \\ \\< Server\>\\< partage$ >\\< nom de fichier\>  
  
 **-o "** C:\Dossier\\<nom_fichier\>"  
  
 Les chemins d'accès aux fichiers comportant des espaces doivent être placés entre guillemets.  
  
 **-r**[**0** | **1**]  
 Redirige la sortie des messages d’erreur à l’écran (**stderr**). Si vous n'indiquez aucun paramètre ou si vous spécifiez la valeur **0**, seuls les messages d'erreur dotés d'un degré de gravité égal ou supérieur à 11 sont redirigés. Si vous indiquez la valeur **1**, tous les messages émis, y compris PRINT, sont redirigés. Est sans effet si vous utilisez - o. Par défaut, les messages sont envoyés à **stdout**.  
  
 **-R**  
 Permet à `sqlcmd` de localiser les colonnes numérique, de devise, de date et heure extraites de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en fonction des paramètres régionaux du client. Par défaut, ces colonnes sont affichées à l'aide des paramètres régionaux du serveur.  
  
 **-u**  
 Spécifie le stockage de *fichier_sortie* au format Unicode, quel que soit le format de *fichier_entrée*.  
  
 **Options relatives à l’exécution de requêtes**  
  **-e**  
 Écrit des scripts d’entrée sur l’appareil de sortie standard (**stdout**).  
  
 **-I**  
 Attribue la valeur ON à l'option de connexion SET QUOTED_IDENTIFIER. La valeur OFF est choisie par défaut. Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).  
  
 **-q"** *requête cmdline* **"**  
 Exécute une requête au démarrage de `sqlcmd`, mais ne quitte pas `sqlcmd` au terme de l'exécution de la requête. Il est possible d'exécuter des requêtes séparées par plusieurs points-virgules. Placez la requête entre guillemets, comme dans l'exemple suivant.  
  
 À l'invite de commandes, tapez :  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  N'utilisez pas le terminateur GO dans la requête.  
  
 Si l'option `-b` est spécifiée avec cette option, `sqlcmd` se termine avec une erreur. L'option `-b` est traitée ultérieurement dans cette rubrique.  
  
 **-Q"** *requête cmdline* **"**  
 Exécute une requête lorsque `sqlcmd` démarre, puis quitte immédiatement `sqlcmd`. Il est possible d'exécuter des requêtes séparées par plusieurs points-virgules.  
  
 Placez la requête entre guillemets, comme dans l'exemple suivant.  
  
 À l'invite de commandes, tapez :  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT FirstName, LastName FROM Person.Person WHERE LastName LIKE 'Whi%';"`  
  
 `sqlcmd -d AdventureWorks2012 -Q "SELECT TOP 5 FirstName FROM Person.Person;SELECT TOP 5 LastName FROM Person.Person;"`  
  
> [!IMPORTANT]  
>  N'utilisez pas le terminateur GO dans la requête.  
  
 Si l'option `-b` est spécifiée avec cette option, `sqlcmd` se termine avec une erreur. L'option `-b` est traitée ultérieurement dans cette rubrique.  
  
 **-t** *délai_expiration_requête*  
 Spécifie le nombre de secondes accordées pour l'exécution d'une commande (ou une instruction SQL). Cette option définit la variable de script `sqlcmd` SQLCMDSTATTIMEOUT. Si une valeur *délai_expiration_requête* n’est pas spécifiée, la commande n’a pas de délai d’expiration. La valeur de *expiration**requête* doit être un nombre compris entre 1 et 65 534. Si la valeur fournie n'est pas numérique ou n'est pas comprise dans cet intervalle, `sqlcmd` génère un message d'erreur.  
  
> [!NOTE]  
>  La valeur de délai d’expiration réelle peut différer de quelques secondes de la valeur *délai_expiration* .  
  
 **-vvar =**  *valeur*[ **var =** *valeur*...]  
 Crée un `sqlcmd`variable de script qui peut être utilisé dans un `sqlcmd` script. Placez la valeur entre guillemets si elle contient des espaces. Vous pouvez spécifier plusieurs ***var***=**»*`values`*»** valeurs. Si l'une des valeurs spécifiées comporte des erreurs, `sqlcmd` génère un message d'erreur et se termine.  
  
 `sqlcmd -v MyVar1=something MyVar2="some thing"`  
  
 `sqlcmd -v MyVar1=something -v MyVar2="some thing"`  
  
 **-x**  
 Permet à `sqlcmd` d'ignorer les variables de script. Cela s’avère utile quand un script contient de nombreuses instructions INSERT pouvant contenir des chaînes dotées du même format que des variables régulières, par exemple $(*nom_variable*).  
  
 **Options relatives à la mise en forme**  
  **-h** *headers*  
 Spécifie le nombre de lignes à imprimer entre les en-têtes de colonne. Par défaut, les en-têtes ne sont imprimés qu'une fois pour chaque jeu de résultats d'une requête. Cette option définit la variable de script `sqlcmd` SQLCMDHEADERS. Utilisez **-1** pour indiquer qu’aucun en-tête ne doit être imprimé. En présence d'une valeur non valide, `sqlcmd` génère un message d'erreur et se termine.  
  
 **-k** [**1** | **2**]  
 Supprime de la sortie tous les caractères de contrôle, par exemple les tabulations et les caractères de nouvelle ligne. Cela préserve la mise en forme des colonnes lorsque des données sont retournées. Si 1 est spécifié, chaque caractère de contrôle est remplacé par un espace. Si 2 est spécifié, les caractères de contrôle consécutifs sont remplacés par un espace. **-k** est identique à **-k1**.  
  
 **-s** *col_separator*  
 Spécifie le caractère de séparation des colonnes. Le caractère espace est utilisé par défaut. Cette option définit la variable de script `sqlcmd` SQLCMDCOLSEP. Pour utiliser des caractères ayant une signification spéciale pour le système d'exploitation, tels que le « et » commercial (&) ou le point-virgule (;), placez ce caractère entre guillemets ("). Le séparateur des colonnes peut être n'importe quel caractère 8 bits.  
  
 **-w** *column_width*  
 Spécifie la largeur d'écran pour la sortie. Cette option définit la variable de script `sqlcmd` SQLCMDCOLWIDTH. La largeur de colonne doit être un nombre supérieur à 8 et inférieur à 65536. Si la largeur de colonne spécifiée ne tombe pas dans cette plage, `sqlcmd` génère un message d'erreur. La largeur par défaut est de 80 caractères. Lorsque la longueur d'une ligne de sortie est supérieure à la largeur de colonne spécifiée, elle revient à la ligne suivante.  
  
 **-W**  
 Cette option supprime les espaces à droite d'une colonne. Utilisez cette option avec l’option **-s** lors de la préparation de données à exporter dans une autre application. Elle ne peut pas être utilisée avec les options **-y** ou **-Y** .  
  
 **-y** *largeur_affichage_type_longueur_variable*  
 Définit la variable de script `sqlcmd` SQLCMDMAXVARTYPEWIDTH. La valeur par défaut est 256. Elle limite le nombre de caractères retournés pour les types de données de longueur variable importante :  
  
-   `varchar(max)`  
  
-   `nvarchar(max)`  
  
-   `varbinary(max)`  
  
-   `xml`  
  
-   `UDT (user-defined data types)`  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
> [!NOTE]  
>  Les types UDT peuvent être de longueur fixe, selon la mise en œuvre. Si cette longueur d’un type UDT à longueur fixe est inférieure à *largeur_affichage*, la valeur du type UDT retournée n’est pas affectée. Cependant, si la longueur est supérieure à *largeur_affichage*, la sortie est tronquée.  
  
 
> [!IMPORTANT]  
>  Utilisez l’option **-y 0** avec une extrême prudence, car elle peut créer de graves problèmes de performances sur le serveur et le réseau, en fonction de la taille des données retournées.  
  
 **-Y** *largeur_affichage_type_longueur_fixe*  
 Définit la variable de script `sqlcmd` SQLCMDMAXFIXEDTYPEWIDTH. La valeur par défaut est 0 (illimitée). Limite le nombre de caractères retournés pour les types de données suivants :  
  
-   `char(` *n* `)`, où 1 < = n < = 8000  
  
-   `nchar(n` *n* `)`, où 1 < = n < = 4000  
  
-   `varchar(n` *n* `)`, où 1 < = n < = 8000  
  
-   `nvarchar(n` *n* `)`, où 1 < = n < = 4000  
  
-   `varbinary(n` *n* `)`, où 1 < = n < = 4000  
  
-   `variant`  
  
 **Options relatives aux rapports d’erreurs**  
  `-b`  
 Spécifie que `sqlcmd` prend fin et retourne une valeur DOS ERRORLEVEL lorsqu'une erreur se produit. La valeur qui est retournée à la variable DOS ERRORLEVEL est **1** lorsque le message d'erreur de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] possède un niveau de gravité supérieur à 10 ; sinon, la valeur retournée est **0**. Si l'option `-V` a été définie en complément de `-b`, `sqlcmd` ne signale pas d'erreur si le niveau de gravité est inférieur aux valeurs définies à l'aide de `-V`. Les fichiers de commande peuvent tester la valeur de ERRORLEVEL et traiter l'erreur d'une manière appropriée. `sqlcmd` ne signale pas d'erreurs pour un niveau de gravité 10 (messages d'information).  
  
 Si le script `sqlcmd` contient un commentaire incorrect, une erreur de syntaxe ou si une variable de script est manquante, la valeur ERRORLEVEL retournée est 1.  
  
 **-m** *error_level*  
 Détermine les messages d’erreur envoyés à **stdout**. Les messages assortis d'un niveau de gravité supérieur ou égal à ce niveau sont envoyés. Quand cette valeur est égale à **-1**, tous les messages, notamment les messages d’information, sont envoyés. Les espaces ne sont pas autorisés entre **-m** et **-1**. Par exemple, **-m-1** est valide, mais **-m-1** ne l’est pas.  
  
 Cette option définit également la variable de script `sqlcmd` SQLCMDERRORLEVEL. La valeur par défaut de cette variable est 0.  
  
 `-V` *error_severity_level*  
 Contrôle le niveau de gravité utilisé pour définir la variable ERRORLEVEL. Les messages d'erreur assortis de niveaux de gravité supérieurs ou égaux à cette valeur définissent ERRORLEVEL. Les valeurs inférieures à 0 sont signalées comme étant 0. La valeur de la variable ERRORLEVEL peut être testée au moyen de fichiers de commandes et CMD.  
  
 **Options diverses**  
  **-a** *packet_size*  
 Demande un paquet d'une taille différente. Cette option définit la variable de script `sqlcmd` SQLCMDPACKETSIZE. *taille_paquet* doit être une valeur comprise entre 512 et 32767. La valeur par défaut est de 4096. Une plus grande taille de paquet peut améliorer les performances d'exécution des scripts comportant un grand nombre d'instructions SQL entre des commandes GO. Vous pouvez demander une taille de paquet plus élevée. Cependant, si la requête est refusée, `sqlcmd` adopte la taille de paquet par défaut du serveur comme taille de paquet.  
  
 **-c** *terminateur_traitement*  
 Spécifie le terminateur de traitement. Par défaut, il faut entrer la commande « GO » sur une ligne isolée pour terminer une commande et la soumettre à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Si vous modifiez de terminateur de traitement, n'utilisez ni les mots clé [!INCLUDE[tsql](../includes/tsql-md.md)] ni les caractères ayant une signification particulière pour le système d'exploitation, qu'ils soient ou non précédés d'une barre oblique inverse  
  
 **-L**[**c**]  
 Répertorie tous les serveurs configurés localement et le nom des serveurs diffusant sur le réseau. Ce paramètre ne peut pas être utilisé en combinaison avec d'autres paramètres. Le nombre maximal de serveurs pouvant être répertoriés est de 3000. Si la liste de serveurs est tronquée en raison de la taille de la mémoire tampon, un message d'avertissement s'affiche.  
  
> [!NOTE]  
>  Compte tenu de la nature de la diffusion sur les réseaux, il est possible que `sqlcmd` ne reçoive pas de réponse de tous les serveurs dans les délais impartis. Par conséquent, la liste des serveurs retournée peut varier à chaque invocation de cette option.  
  
 Si le paramètre optionnel **c** est spécifié, la sortie s'affiche sans les serveurs : la ligne d'en-tête et chaque ligne de serveur apparaissent sans espace de début. La sortie est alors dite « propre ». Une sortie propre améliore les performances de traitement des langages de script.  
  
 **-p**[**1**]  
 Imprime des statistiques de performances pour chaque jeu de résultats. L'exemple suivant illustre le format des statistiques de performances :  
  
 `Network packet size (bytes): n`  
  
 `x xact[s]:`  
  
 `Clock Time (ms.): total       t1  avg       t2 (t3 xacts per sec.)`  
  
 Où :  
  
 `x` = Nombre de transactions traitées par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 `t1` = Durée totale de toutes les transactions.  
  
 `t2` = Durée moyenne d’une transaction spécifique.  
  
 `t3` = Nombre moyen de transactions par seconde.  
  
 Toutes les durées sont exprimées en millisecondes.  
  
 Si le paramètre facultatif **1** est spécifié, les statistiques sont séparées par deux points et peuvent être aisément importées dans une feuille de calcul ou traitées par un script.  
  
 Si le paramètre facultatif correspond à n’importe quelle valeur autre que **1**, une erreur est générée et `sqlcmd` se termine.  
  
 `-X`[**1**]  
 Désactive les commandes pouvant compromettre la sécurité du système lorsque `sqlcmd` est exécuté à partir d'un fichier de commandes. Les commandes désactivées sont toujours reconnues ; `sqlcmd` émet un message d'avertissement et continue. Si le paramètre facultatif **1** est spécifié, `sqlcmd` génère un message d’erreur, puis se termine. Les commandes suivantes sont désactivées lorsque l'option `-X` est utilisée :  
  
-   **ED**  
  
-   **!!** *commande*  
  
 Si l'option `-X` est spécifiée, elle empêche le passage des variables d'environnement à `sqlcmd`. Elle interdit également l'exécution du script de démarrage spécifié au moyen de la variable de script SQLCMDINI. Pour plus d’informations sur `sqlcmd` variables de script, consultez [utiliser sqlcmd avec des Variables de script](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md).  
  
 **-?**  
 Affiche le résumé de la syntaxe des options de `sqlcmd`.  
  
## <a name="remarks"></a>Notes  
 Les options ne doivent pas nécessairement être utilisées dans l'ordre indiqué dans la section de la syntaxe.  
  
 Lorsque plusieurs résultats sont retournés, `sqlcmd` imprime une ligne vide entre chaque ensemble de résultats dans un traitement. En outre, le «\<x > lignes affectées « message n’apparaît pas lorsqu’il ne concerne pas l’instruction exécutée.  
  
 Pour utiliser `sqlcmd` de façon interactive, tapez `sqlcmd` à l’invite de commande avec une ou plusieurs des options décrites plus haut dans cette rubrique. Pour plus d’informations, consultez [Utiliser l’utilitaire sqlcmd](../relational-databases/scripting/sqlcmd-use-the-utility.md).  
  
> [!NOTE]  
>  Les options **-L**, **-Q**, **-Z** ou **-i** provoquer `sqlcmd` quitte après l’exécution.  
  
 La longueur totale de la ligne de commande `sqlcmd` dans l'environnement de commande (Cmd.exe), comprenant tous les arguments et les variables développées, est la longueur déterminée par le système d'exploitation pour Cmd.exe.  
  
## <a name="variable-precedence-low-to-high"></a>Priorité des variables (faible à élevée)  
  
1.  Variables d'environnement au niveau du système.  
  
2.  Variables d'environnement au niveau de l'utilisateur.  
  
3.  Interface de commande (**définir** X = Y) défini à l’invite de commande avant d’exécuter `sqlcmd`.  
  
4.  **sqlcmd-v** X=Y  
  
5.  **:Setvar** X Y  
  
> [!NOTE]  
>  Pour afficher les variables d’environnement, dans le **Panneau de configuration**, ouvrez **Système**, puis cliquez sur l’onglet **Avancé** .  
  
## <a name="sqlcmd-scripting-variables"></a>Variables de script sqlcmd  
  
|Variable|Commutateur associé|R/W (Lecture/écriture)|Valeur par défaut|  
|--------------|--------------------|----------|-------------|  
|SQLCMDUSER|-U|R|""|  
|SQLCMDPASSWORD|-P|--|""|  
|SQLCMDSERVER|-S|R|"DefaultLocalInstance"|  
|SQLCMDWORKSTATION|-H|R|"ComputerName"|  
|SQLCMDDBNAME|-d|R|""|  
|SQLCMDLOGINTIMEOUT|-l|R/W (Lecture/écriture)|"8" (secondes)|  
|SQLCMDSTATTIMEOUT|-t|R/W (Lecture/écriture)|"0" = Attendre indéfiniment|  
|SQLCMDHEADERS|-H|R/W (Lecture/écriture)|"0"|  
|SQLCMDCOLSEP|-S|R/W (Lecture/écriture)|« »|  
|SQLCMDCOLWIDTH|-w|R/W (Lecture/écriture)|"0"|  
|SQLCMDPACKETSIZE|-A|R|"4096"|  
|SQLCMDERRORLEVEL|-M|R/W (Lecture/écriture)|0|  
|SQLCMDMAXVARTYPEWIDTH|-y|R/W (Lecture/écriture)|"256"|  
|SQLCMDMAXFIXEDTYPEWIDTH|-y|R/W (Lecture/écriture)|"0" = illimitée|  
|SQLCMDEDITOR||R/W (Lecture/écriture)|"edit.com"|  
|SQLCMDINI||R|""|  
  
 Les variables SQLCMDUSER, SQLCMDPASSWORD et SQLCMDSERVER sont définies lorsque la commande **:Connect**  
  
 est utilisée.  
  
 R indique que la valeur ne peut être définie qu'une seule fois lors de l'initialisation du programme.  
  
 R/W (« Lecture/écriture ») indique que la valeur peut être modifiée à l’aide de la commande **setvar** et que les commandes ultérieures sont tributaires de la nouvelle valeur.  
  
## <a name="sqlcmd-commands"></a>Commandes sqlcmd  
 En complément des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] dans `sqlcmd`, vous pouvez également utiliser les commandes ci-dessous :  
  
|||  
|-|-|  
|**GO** [*count*]|**:List**|  
|[**:**] **RESET**|**:Error**|  
|[**:**] **ED**|**:Out**|  
|[**:**] **!!**|**:Perftrace**|  
|[**:**] **QUIT**|**:Connect**|  
|[**:**] **EXIT**|**:On Error**|  
|**:r**|**:Help**|  
|**:ServerList**|**:XML** [**ON** &#124; **OFF**]|  
|**:Setvar**|**:Listvar**|  
  
 Tenez compte des éléments suivants lorsque vous utilisez des commandes `sqlcmd` :  
  
-   Toutes les commandes `sqlcmd`, à l'exception de GO, doivent posséder deux points (:) comme préfixe.  
  
    > [!IMPORTANT]  
    >  Pour assurer la compatibilité descendante avec les scripts **osql** existants, certaines commandes sont reconnues sans les deux-points. Ceci est indiqué par la notation [**:**].  
  
-   Les commandes `sqlcmd` ne sont reconnues que si elles apparaissent au début d'une ligne.  
  
-   Toutes les commandes `sqlcmd` ne respectent pas la casse.  
  
-   Chaque commande doit figurer sur une ligne séparée. Une commande ne peut pas être suivie d'une instruction [!INCLUDE[tsql](../includes/tsql-md.md)] ou d'une autre commande.  
  
-   Les commandes sont exécutées immédiatement. Elles ne sont pas placées dans le tampon d'exécution contrairement aux instructions [!INCLUDE[tsql](../includes/tsql-md.md)] .  
  
 **Commandes d’édition**  
  [**:**] **ED**  
 Démarre l'éditeur de texte. Cet éditeur peut être employé pour modifier le lot [!INCLUDE[tsql](../includes/tsql-md.md)] actuel ou le dernier traitement exécuté. Pour modifier le dernier traitement exécuté, la commande **ED** doit être tapée immédiatement après la fin de l'exécution du dernier traitement.  
  
 L'éditeur de texte est défini dans la variable d'environnement SQLCMDEDITOR. L'éditeur par défaut est « edit ». Pour modifier l'éditeur, définissez la variable SQLCMDEDITOR. Par exemple, pour choisir l'éditeur Bloc-notes [!INCLUDE[msCoName](../includes/msconame-md.md)] , à l'invite de commandes, tapez :  
  
 `SET SQLCMDEDITOR=notepad`  
  
 [**:**] **RESET**  
 Vide le cache d'instruction.  
  
 **:List**  
 Imprime le contenu du cache d'instruction.  
  
 **Variables**  
  **: Setvar** \< **var**> [ **»*`value`*»** ]  
 Définit des variables de script `sqlcmd`. Les variables de script possèdent le format suivant : `$(VARNAME)`.  
  
 Les noms de variable ne respectent pas la casse.  
  
 Les variables de script peuvent être définies comme suit :  
  
-   Implicitement à l'aide d'une option de ligne de commande. Par exemple, le **-l** option définit la SQLCMDLOGINTIMEOUT `sqlcmd` variable.  
  
-   Explicitement à l'aide de la commande **:Setvar** .  
  
-   En définissant une variable d'environnement avant d'exécuter `sqlcmd`.  
  
> [!NOTE]  
>  L'option `-X` empêche le transfert des variables d'environnement vers `sqlcmd`.  
  
 Si une variable définie à l'aide de **:Setvar** et une variable d'environnement possèdent le même nom, la variable définie à l'aide de **:Setvar** est prioritaire.  
  
 Les noms de variable ne doivent pas contenir de caractères espace.  
  
 Les noms de variables ne peuvent pas posséder la même forme qu'une expression variable, telle que $(var).  
  
 Si une valeur de chaîne de la variable de script contient des espaces, placez la valeur entre guillemets. Si aucune valeur n'est spécifiée pour une variable de script, cette dernière est supprimée.  
  
 **:Listvar**  
 Affiche la liste des variables de script actuellement définies.  
  
> [!NOTE]  
>  Seules les variables qui sont définies par de script `sqlcmd`et celles qui sont définies à l’aide de la **: Setvar** commande s’affiche.  
  
 **Commandes de sortie**  
  **:Error**   
 ***\<***  *nom_fichier*  ***>|* STDERR|STDOUT**  
 Redirige l’ensemble de la sortie d’erreur dans le fichier spécifié par *nom_fichier*vers **stderr** ou vers **stdout**. La commande **Error** peut apparaître plusieurs fois dans un script. Par défaut, la sortie d'erreur est envoyée à **stderr**.  
  
 *nom de fichier*  
 Crée et ouvre un fichier destiné à recevoir la sortie. Si le fichier existe déjà, il est tronqué à zéro octet. Si le fichier n'est pas disponible car des autorisations sont requises, ou pour d'autres raisons, la sortie n'est pas modifiée, et elle est envoyée à la dernière destination spécifiée ou à la destination par défaut.  
  
 **STDERR**  
 Dirige la sortie d’erreur vers le flux **stderr** . Si cette destination a été redirigée, la cible de cette redirection reçoit la sortie d'erreur.  
  
 **STDOUT**  
 Fait basculer la sortie d’erreur vers le flux **stdout** . Si cette destination a été redirigée, la cible de cette redirection reçoit la sortie d'erreur.  
  
 **:Out \<** *nom_fichier* **>**| **STDERR**| **STDOUT**  
 Crée et redirige l’ensemble des résultats de requête dans le fichier spécifié par *nom_fichier*vers **stderr** ou vers **stdout**. Par défaut, la sortie est envoyée à **stdout**. Si le fichier existe déjà, il est tronqué à zéro octet. La commande **Out** peut apparaître plusieurs fois dans un script.  
  
 **:Perftrace \<** *nom_fichier* **>**| **STDERR**| **STDOUT**  
 Crée et redirige l’ensemble des informations de traces de performances dans le fichier spécifié par *nom_fichier*vers **stderr** ou vers **stdout**. Par défaut, la sortie de traces de performances est envoyée à **stdout**. Si le fichier existe déjà, il est tronqué à zéro octet. La commande **Perftrace** peut apparaître plusieurs fois dans un script.  
  
 **Commandes de contrôle d’exécution**  
  **: En cas d’erreur**[ `exit`  |  `ignore`]  
 Définit l'action à effectuer lorsqu'une erreur se produit en cours de script ou d'exécution d'un traitement.  
  
 Lorsque l'option `exit` est employée, `sqlcmd` se termine avec la valeur d'erreur appropriée.  
  
 Lorsque l'option `ignore` est employée, `sqlcmd` ignore l'erreur et poursuit l'exécution du traitement ou du script. Par défaut, un message d'erreur est imprimé.  
  
 [**:**] **QUIT**  
 Provoque la fin de `sqlcmd`.  
  
 [**:**] **EXIT**[ **(*`statement`*)** ]  
 Vous permet d'utiliser le résultat d'une instruction SELECT comme valeur de retour de `sqlcmd`. S'il est numérique, la première colonne de la dernière ligne de résultats est convertie en un entier de 4 octets (entier long). MS-DOS transmet l'octet de poids faible au processus parent ou au niveau erreur du système d'exploitation. Windows 200x transmet la totalité de l'entier de 4 octets. La syntaxe de cette commande est la suivante :  
  
 `:EXIT(query)`  
  
 Exemple :  
  
 `:EXIT(SELECT @@ROWCOUNT)`  
  
 Vous pouvez également inclure le paramètre **EXIT** dans un fichier de commandes. Par exemple, à l'invite de commandes, tapez :  
  
 `sqlcmd -Q "EXIT(SELECT COUNT(*) FROM '%1')"`  
  
 Le `sqlcmd` utilitaire envoie tout le contenu entre parenthèses **()** sur le serveur. Si une procédure stockée système sélectionne un ensemble et retourne une valeur, seule la sélection est retournée. L’instruction EXIT **()** sans information entre parenthèses exécute toutes les commandes qui la précèdent dans le traitement, puis se termine sans valeur de retour.  
  
 Lorsqu'une requête incorrecte est spécifiée, `sqlcmd` se termine sans valeur de retour.  
  
 Liste des formats EXIT :  
  
-   :EXIT  
  
 N'exécute pas le traitement, puis se termine immédiatement sans retourner de valeur.  
  
-   :EXIT( )  
  
 Exécute le traitement, puis quitte sans retourner de valeur.  
  
-   :EXIT(requête)  
  
 Exécute le traitement qui inclut la requête, puis se termine après avoir retourné les résultats de la requête.  
  
 Si RAISERROR est utilisé dans un `sqlcmd` script et une erreur de gravité 127 se produit, `sqlcmd` se termine et l’ID de message au client. Exemple :  
  
 `RAISERROR(50001, 10, 127)`  
  
 Cette erreur arrête l'exécution du script `sqlcmd` et envoie au client le message 50001.  
  
 Les valeurs retournées de -1 à -99 sont réservées à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ; `sqlcmd` définit les valeurs suivantes :  
  
|Valeurs de retour|Description|  
|-------------------|-----------------|  
|-100|Erreur rencontrée avant la sélection d'une valeur retournée.|  
|-101|Aucune ligne trouvée lors de la sélection d'une valeur retournée.|  
|-102|Erreur de conversion survenue lors de la sélection d'une valeur retournée.|  
  
 **GO** [*count*]  
 GO indique la fin d'un traitement et l'exécution des commandes [!INCLUDE[tsql](../includes/tsql-md.md)] placées dans le cache. Lors de la spécification d'une valeur pour *count*, les instructions mises en mémoire cache sont exécutées *count* fois, comme un traitement unique.  
  
 **Commandes diverses**  
  **:r \<** *filename* **>**  
 Analyse supplémentaire [!INCLUDE[tsql](../includes/tsql-md.md)] instructions et `sqlcmd` commandes à partir du fichier spécifié par **< *`filename`* >** dans le cache d’instruction.  
  
 Si le fichier contient des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] qui ne sont pas suivies par **GO**, vous devez entrer **GO** sur la ligne qui suit **:r**.  
  
> [!NOTE]  
>  **\<** *nom de fichier* **>** est lu par rapport au répertoire de démarrage dans lequel `sqlcmd` a été exécuté.  
  
 Le fichier est lu et exécuté après la rencontre d'un terminateur de traitement. Vous pouvez émettre plusieurs commandes **:r** . Le fichier peut inclure une commande `sqlcmd`. Elle inclut le terminateur de traitement **GO**.  
  
> [!NOTE]  
>  Le nombre de lignes affichées en mode interactif augmente de 1 chaque fois qu'une commande **:r** est rencontrée. La commande **:r** apparaît dans la sortie de la commande list.  
  
 **:Serverlist**  
 Répertorie tous les serveurs configurés localement et les noms des serveurs émettant sur le réseau.  
  
 **:Connect**  *server_name*[**\\***instance_name*] [-l *timeout*] [-U *user_name* [-P *password*]]  
 Établit une connexion à une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Ferme également la connexion actuelle.  
  
 Options de délai :  
  
|||  
|-|-|  
|0|attendre indéfiniment|  
|n>0|attendre n secondes|  
  
 La variable de script SQLCMDSERVER reflète la connexion active actuelle.  
  
 Si l'argument *timeout* n'est pas spécifié, la valeur de la variable SQLCMDLOGINTIMEOUT est la valeur par défaut.  
  
 Si seulement *nom_utilisateur* est spécifié (en tant qu’option ou en tant que variable d’environnement), un message invite l’utilisateur à entrer un mot de passe. Cela ne s'applique pas si les variables d'environnement SQLCMDUSER ou SQLCMDPASSWORD ont été définies. Si ni les options ni les variables d'environnement ne sont fournies, le mode d'authentification Windows est employé pour se connecter. Par exemple, pour établir une connexion à une instance, `instance1`, de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], `myserver`, en utilisant à la sécurité intégrée, vous devez utiliser ce qui suit :  
  
 `:connect myserver\instance1`  
  
 Pour établir une connexion à l'instance par défaut de `myserver` en utilisant des variables de script, utilisez ce qui suit :  
  
 `:setvar myusername test`  
  
 `:setvar myservername myserver`  
  
 `:connect $(myservername) $(myusername)`  
  
 [**:**] **!!**  \< *commande*>  
 Exécute des commandes du système d'exploitation. Pour exécuter une commande du système d’exploitation, commencez une ligne par deux points d’exclamation (**!!**) suivis de la commande du système d’exploitation. Exemple :  
  
 `:!! Dir`  
  
> [!NOTE]  
>  La commande est exécutée sur l'ordinateur sur lequel `sqlcmd` s'exécute.  
  
 **:XML** [**ON** | **OFF**]  
 Pour plus d'informations, consultez « Format de sortie XML », plus loin dans cette rubrique.  
  
 **:Help**  
 Répertorie les commandes `sqlcmd` avec une brève description de chaque commande.  
  
### <a name="sqlcmd-file-names"></a>Noms de fichiers sqlcmd  
 `sqlcmd` fichiers d’entrée peuvent être spécifiés avec le **-i** option ou **: r** commande. Les fichiers de sortie peuvent être spécifiés avec l’option **-o** ou les commandes **:Error**, **:Out** et **:Perftrace** . Voici quelques consignes relatives à l'utilisation de ces fichiers :  
  
-   **: Erreur**, **: Out** et **: Perftrace** doit utiliser distinct **< *`filename`* >**. Si le même **< *`filename`* >** est utilisé, les entrées à partir des commandes peuvent être mélangées.  
  
-   Si un fichier d'entrée situé sur un serveur distant est appelé à partir de `sqlcmd` sur un ordinateur local et s'il contient un chemin d'accès de fichier sur un lecteur tel que :out c:\OutputFile.txt, ce fichier de sortie sera créé sur l'ordinateur local et non sur le serveur distant.  
  
-   Chemins de fichier valides incluent : C:\\**<*`filename`*>**, \\ \\< Server\> \\ < partage$ >\\ **< *`filename`* >** et « dossier de C:\Some\\  **<  *`file name`*>**". Si le chemin d'accès comporte un espace, utilisez des guillemets.  
  
-   Chaque nouvelle session `sqlcmd` remplace les fichiers existants qui ont des noms identiques.  
  
### <a name="informational-messages"></a>Messages d'information  
 `sqlcmd` imprime les messages d'information envoyés par le serveur. Dans l'exemple suivant, après l'exécution des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] , un message d'information est imprimé.  
  
 À l'invite de commandes, tapez :  
  
 `sqlcmd`  
  
 `At the sqlcmd prompt type:`  
  
 `USE AdventureWorks2012;`  
  
 `GO`  
  
 Lorsque vous appuyez sur Entrée, le message d'information suivant s'imprime : « Le contexte de la base de données a été modifié et correspond à présent à 'AdventureWorks2012' ».  
  
### <a name="output-format-from-transact-sql-queries"></a>Format de sortie des requêtes Transact-SQL  
 `sqlcmd` imprime tout d'abord un en-tête de colonne qui contient les noms de colonne spécifiés dans la liste de sélection. Les noms de colonne sont séparés avec le caractère SQLCMDCOLSEP. Par défaut, il s'agit d'un espace. Si le nom de colonne est plus court que la largeur de colonne, la sortie est complétée avec des espaces jusqu'à la colonne suivante.  
  
 Cette ligne est suivie d'un séparateur de ligne qui correspond à une série de tirets. La sortie suivante constitue un exemple.  
  
 Démarrez `sqlcmd`. À l'invite de commandes `sqlcmd`, tapez :  
  
 `USE AdventureWorks2012;`  
  
 `SELECT TOP (2) BusinessEntityID, FirstName, LastName`  
  
 `FROM Person.Person;`  
  
 `GO`  
  
 Lorsque vous appuyez sur Entrée, le jeu de résultats suivant est retourné.  
  
 `BusinessEntityID FirstName    LastName`  
  
 `---------------- ------------ ----------`  
  
 `285              Syed         Abbas`  
  
 `293              Catherine    Abel`  
  
 `(2 row(s) affected)`  
  
 Bien que la colonne `BusinessEntityID` ne possède que 4 caractères de large, elle a été étendue pour contenir le nom de colonne plus long. Par défaut, la sortie se termine à 80 caractères. Vous pouvez modifier ceci en utilisant l’option **-w** ou en définissant la variable de script SQLCMDCOLWIDTH.  
  
### <a name="xml-output-format"></a>Format de sortie XML  
 La sortie XML qui est le résultat d'une clause FOR XML est générée, sans mise en forme, dans un flux continu.  
  
 Lorsque vous attendez une sortie XML, utilisez la commande suivante : `:XML ON`.  
  
> [!NOTE]  
>  `sqlcmd` retourne des messages d'erreur au format habituel. Notez que les messages d'erreur sont également une sortie dans le flux de texte XML au format XML. Avec `:XML ON`, `sqlcmd` n'affiche aucun message d'information.  
  
 Pour désactiver le mode XML, utilisez la commande suivante : `:XML OFF`  
  
 La commande GO ne doit pas apparaître avant la commande XML OFF, car cette dernière remet `sqlcmd` en sortie orientée ligne.  
  
 Les données XML (diffusées en continu) et les données d'ensemble de lignes ne peuvent être mélangées. Si la commande XML ON n'a pas été émise avant l'exécution d'une instruction [!INCLUDE[tsql](../includes/tsql-md.md)] qui génère des flux XML, la sortie est incohérente. Si la commande XML ON a été émise, vous ne pouvez pas exécuter des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] qui produisent des ensembles de lignes réguliers.  
  
> [!NOTE]  
>  La commande **:XML** ne prend pas en charge l’instruction SET STATISTICS XML.  
  
## <a name="sqlcmd-best-practices"></a>Méthodes conseillées sqlcmd  
 Utilisez les méthodes suivantes pour optimiser la sécurité et l'efficacité.  
  
-   Utilisez la sécurité intégrée.  
  
-   Utilisez `-X` dans des environnements automatisés.  
  
-   Protégez les fichiers d'entrée et de sortie à l'aide des autorisations appropriées du système de fichiers NTFS.  
  
-   Pour accroître les performances, effectuez autant d'opérations que possible au sein d'une session `sqlcmd` au lieu de recourir à une série de sessions.  
  
-   Pour l'exécution de requête ou de traitement, définissez des valeurs de délai supérieures à la durée que vous prévoyez pour l'exécution du traitement ou de la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer l’utilitaire sqlcmd](../relational-databases/scripting/sqlcmd-start-the-utility.md)   
 [Exécuter des fichiers de script Transact-SQL à l’aide de sqlcmd](../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md)   
 [Utiliser l’utilitaire sqlcmd](../relational-databases/scripting/sqlcmd-use-the-utility.md)   
 [Utiliser sqlcmd avec des variables de script](../relational-databases/scripting/sqlcmd-use-with-scripting-variables.md)   
 [Se connecter au moteur de base de données avec sqlcmd](../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)   
 [Modifier des scripts SQLCMD à l’aide de l’Éditeur de requête](../relational-databases/scripting/edit-sqlcmd-scripts-with-query-editor.md)   
 [Gérer les étapes de travail](../ssms/agent/manage-job-steps.md)   
 [Créer une étape de travail CmdExec](../ssms/agent/create-a-cmdexec-job-step.md)  
  
  
