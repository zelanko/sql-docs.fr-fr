---
title: Connexion avec sqlcmd | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sqlcmd
ms.assetid: 61a2ec0d-1bcb-4231-bea0-cff866c21463
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 48e4771b8d538775ae2e2faec053f0263bd6d653
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66789889"
---
# <a name="connecting-with-sqlcmd"></a>Connexion avec sqlcmd
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

L’utilitaire [sqlcmd](https://go.microsoft.com/fwlink/?LinkID=154481) est disponible dans [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS.
  
Les commandes suivantes montrent comment utiliser l’authentification Windows (Kerberos) et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l’authentification, respectivement :
  
```  
sqlcmd -E -Sxxx.xxx.xxx.xxx  
sqlcmd -Sxxx.xxx.xxx.xxx -Uxxx -Pxxx  
```  
  
## <a name="available-options"></a>Options disponibles

Dans la version actuelle, les options suivantes sont disponibles :  
  
- -? Affichage `sqlcmd` utilisation.  
  
- -a Demander une taille de paquet.  
  
- -b Arrêter le traitement par lots en cas d’erreur.  
  
- -c *batch_terminator* spécifier le terminateur de lot.  
  
- -C Faire confiance au certificat de serveur.  

- -d *database_name* problème un `USE` *database_name* instruction lorsque vous démarrez `sqlcmd`.  

- -D Fait en sorte que la valeur passée à l’option -S de `sqlcmd` soit interprétée comme un nom de source de données (DSN). Pour plus d’informations, consultez « Prise en charge du nom de source de données dans `sqlcmd` et `bcp` » à la fin de cette rubrique.  
  
- -e Écrire des scripts d’entrée sur le périphérique de sortie standard (stdout).

- Utiliser la connexion approuvée et l’authentification intégrée. Pour plus d’informations sur les connexions approuvées qui utilisent l’authentification intégrée à partir d’un client Linux ou macOS, consultez [à l’aide de l’authentification intégrée](../../../connect/odbc/linux-mac/using-integrated-authentication.md).

- -h *nombre_de_lignes*  Spécifier le nombre de lignes à imprimer entre les en-têtes de colonnes.  
  
- -H Spécifier un nom de station de travail.  
  
- -i *input_file*[,*input_file*[,...]] Identifier le fichier contenant un traitement d'instructions SQL ou des procédures stockées.  
  
- -J’ensemble la `SET QUOTED_IDENTIFIER` option de connexion sur ON.  
  
- -k Supprimer ou remplacer des caractères de contrôle.  
  
- **-K**_application\_intent_  
Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. La seule valeur actuellement prise en charge est **ReadOnly**. Si vous ne spécifiez pas **-K**, `sqlcmd` ne prend pas en charge la connectivité à un réplica secondaire dans un groupe de disponibilité AlwaysOn. Pour plus d’informations, consultez [Prise en charge par le pilote ODBC pour Linux de la haute disponibilité et de la reprise d’activité](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
> [!NOTE]  
> L’option **-K** n’est pas prise en charge dans le CTP pour SUSE Linux. Vous pouvez toutefois spécifier le mot clé **ApplicationIntent=ReadOnly** dans un fichier DSN passé à `sqlcmd`. Pour plus d’informations, consultez « Prise en charge du nom de source de données dans `sqlcmd` et `bcp` » à la fin de cette rubrique.  
  
- -l *timeout* spécifie le nombre de secondes au terme duquel une connexion `sqlcmd` expire quand vous tentez de vous connecter à un serveur.

- -m *niveau_erreur* Déterminer les messages d’erreur envoyés à stdout.  
  
- **-M**_multisubnet\_failover_  
Spécifiez toujours **-M** en cas de connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. **-M** accélère la détection des basculements et la connexion au serveur (actuellement) actif. Si vous ne spécifiez pas l’option **-M** , **-M** est désactivé. Pour plus d’informations sur [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)], consultez [pilote ODBC sur Linux et macOS - haute disponibilité et récupération d’urgence](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
> [!NOTE]  
> L’option **-M** n’est pas prise en charge dans le CTP pour SUSE Linux. Vous pouvez toutefois spécifier le mot clé **MultiSubnetFailover=Yes** dans un fichier DSN passé à `sqlcmd`. Pour plus d’informations, consultez « Prise en charge du nom de source de données dans `sqlcmd` et `bcp` » à la fin de cette rubrique.  
  
- -N Chiffrer la connexion.  
  
- -o *fichier_sortie* Identifier le fichier qui reçoit le sortie de `sqlcmd`.  
  
- -p Imprimer des statistiques de performances pour chaque jeu de résultats.  
  
- -P Spécifier un mot de passe utilisateur.  
  
- -q *commandline_query* exécuter une requête lorsque `sqlcmd` démarre, mais ne quitte pas une fois la requête en cours d’exécution.  

- -Q *commandline_query* exécuter une requête lorsque `sqlcmd` démarre. `sqlcmd` s’arrête quand la requête est terminée.  

- -r Redirige les messages d’erreur vers stderr.

- -R Fait en sorte que le pilote utilise les paramètres régionaux du client pour convertir les données de devise et de date et d’heure en données caractères. Uniquement actuellement uniquement la mise en forme en_US (anglais américain).
  
- s - *column_separator_char* spécifier le caractère de séparation des colonnes.  

- -S [*protocol*:] *server*[ **,** _port_]  
Spécifiez l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour se connecter à, ou si -D est utilisé, une source de données. Le pilote ODBC sur Linux et macOS nécessite - S. Notez que **tcp** est le seul protocole valide.  
  
- -t *délai_expiration_requête* Spécifier le nombre de secondes accordées pour l’exécution d’une commande (ou une instruction SQL).  
  
- -u Spécifier que fichier_sortie est stocké au format Unicode, quel que soit le format de fichier_entrée.  
  
- -U *login_id* spécifier un ID de connexion utilisateur.  
  
- -V *niveau_gravité_erreur* Contrôler le niveau de gravité utilisé pour définir la variable ERRORLEVEL.  
  
- -w *largeur_de_colonne* spécifier la largeur d’écran de sortie.  
  
- -W Supprimer les espaces à droite d’une colonne.  
  
- -x Désactiver la substitution de variable.  
  
- -X Désactiver les commandes, le script de démarrage et les variables d’environnement.  
  
- -y *variable_length_type_display_width* définir le `sqlcmd` variable de script `SQLCMDMAXFIXEDTYPEWIDTH`.
  
- -Y *fixed_length_type_display_width* définir le `sqlcmd` variable de script `SQLCMDMAXVARTYPEWIDTH`.


## <a name="available-commands"></a>Commandes disponibles

Dans la version actuelle, les commandes suivantes sont disponibles :  
  
-   [:]!!  
  
-   :Connect  
  
-   :Error  
  
-   [:]EXIT  
  
-   GO [*count*]  
  
-   :Help  
  
-   :List  
  
-   :Listvar  
  
-   :On Error  
  
-   :Out  
  
-   :Perftrace  
  
-   [:]QUIT  
  
-   :r  
  
-   :RESET  
  
-   :setvar  
  
## <a name="unavailable-options"></a>Options non disponibles
Dans la version actuelle, les options suivantes ne sont pas disponibles :  

- -A Se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec une connexion administrateur dédiée (DAC). Pour plus d’informations sur la façon d’établir une connexion administrateur dédiée, consultez [Recommandations en matière de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md).  
  
- -f *page_de_code* Spécifier les pages de codes d’entrée et de sortie.  
  
- -L Répertorier les serveurs configurés localement et le nom des serveurs diffusant sur le réseau.  
  
- -v Créer une variable de script `sqlcmd` pouvant être utilisée dans un script `sqlcmd`.  
  
Vous pouvez utiliser la méthode alternative suivante : placez les paramètres dans un seul fichier, ce qui vous pouvez ensuite ajouter à un autre fichier. Cela vous aidera à utiliser un fichier de paramètres pour remplacer les valeurs. Par exemple, créer un fichier nommé `a.sql` (le fichier de paramètres) avec le contenu suivant :
  
    :setvar ColumnName object_id  
    :setvar TableName sys.objects  
  
Ensuite, créer un fichier nommé `b.sql` avec les paramètres de remplacement :  
  
    select $(ColumnName) from $(TableName)  

Sur la ligne de commande combiner `a.sql` et `b.sql` dans `c.sql` utilisant les commandes suivantes :  
  
    cat a.sql > c.sql 
  
    cat b.sql >> c.sql  
  
Exécutez `sqlcmd` et utiliser `c.sql` en tant que fichier d’entrée :  
  
    slqcmd -S<...> -P<..> -U<..> -I c.sql  

- z - *mot de passe* Change password.  
  
- Z - *mot de passe* modifier le mot de passe et quitter.  

## <a name="unavailable-commands"></a>Commandes non disponibles

Dans la version actuelle, les commandes suivantes ne sont pas disponibles :  
  
-   :ED  
  
-   :ServerList  
  
-   :XML  
  
## <a name="dsn-support-in-sqlcmd-and-bcp"></a>Prise en charge du nom de source de données dans sqlcmd et bcp

Vous pouvez spécifier un nom de source de données plutôt qu’un nom de serveur dans l’option **sqlcmd** ou **bcp** `-S` (ou la commande **sqlcmd** :Connect) si vous spécifiez -D. D - provoque **sqlcmd** ou **bcp** pour se connecter au serveur spécifié dans la source de données par l’option -S.  
  
Sources de données système sont stockés dans le `odbc.ini` fichier dans le répertoire ODBC SysConfigDir (`/etc/odbc.ini` sur les installations standard). Sources de données utilisateur sont stockés dans `.odbc.ini` dans un répertoire de base (`~/.odbc.ini`).
  
Les entrées suivantes sont prises en charge dans un nom de source de données sur Linux ou macOS :

-   **ApplicationIntent=ReadOnly**  

-   **Base de données =** _base de données\_nom_  
  
-   **Pilote = ODBC Driver 11 pour SQL Server** ou **pilote = ODBC Driver 13 pour SQL Server**
  
-   **MultiSubnetFailover=Yes**  
  
-   **Server=** _server\_name\_or\_IP\_address_  
  
-   **Trusted_Connection=yes**|**no**  
  
Dans un nom de source de données, seule l’entrée DRIVER est nécessaire, mais pour établir une connexion à un serveur, `sqlcmd` ou `bcp` a besoin de la valeur de l’entrée SERVER.  

Si vous spécifiez la même option dans le nom de source de données et sur la ligne de commande `sqlcmd` ou `bcp`, l’option de ligne de commande remplace la valeur utilisée dans le nom de source de données. Par exemple, si le nom de source de données comporte une entrée DATABASE et que la ligne de commande `sqlcmd` inclut **-d**, la valeur passée à **-d** est utilisée. Si vous spécifiez **Trusted_Connection=yes** dans le nom de source de données, l’authentification Kerberos est utilisée et le nom d’utilisateur ( **-U**) et le mot de passe ( **-P**), s’ils sont fournis, sont ignorés.

Vous pouvez modifier les scripts qui appellent `isql` pour qu’ils utilisent `sqlcmd` en définissant l’alias suivant : `alias isql="sqlcmd -D"`.  

## <a name="see-also"></a>Voir aussi  
[Connexion avec **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md)  
 
