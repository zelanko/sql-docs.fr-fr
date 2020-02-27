---
title: Se connecter à sqlcmd | Microsoft Docs
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
ms.openlocfilehash: c73ee7914d0d9ac560d57a204458e5cd4ba57a0d
ms.sourcegitcommit: 1b0906979db5a276b222f86ea6fdbe638e6c9719
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971446"
---
# <a name="connecting-with-sqlcmd"></a>Connexion avec sqlcmd
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

L’utilitaire [sqlcmd](https://go.microsoft.com/fwlink/?LinkID=154481) est disponible dans [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS.
  
Les commandes suivantes montrent respectivement comment utiliser l’authentification Windows (Kerberos) l’authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] :
  
```  
sqlcmd -E -Sxxx.xxx.xxx.xxx  
sqlcmd -Sxxx.xxx.xxx.xxx -Uxxx -Pxxx  
```  
  
## <a name="available-options"></a>Options disponibles

Dans la version actuelle, les options suivantes sont disponibles :  
  
- -? Afficher l’utilisation de `sqlcmd`.  
  
- -a Demander une taille de paquet.  
  
- -b Arrêter le traitement par lots en cas d’erreur.  
  
- -c *marque_fin_lot* Spécifier la marque de fin de lot.  
  
- -C Faire confiance au certificat de serveur.  

- -d *nom_base_de_données* Émettre une instruction `USE` *nom_base_de_données* au démarrage de `sqlcmd`.  

- -D Fait en sorte que la valeur passée à l’option -S de `sqlcmd` soit interprétée comme un nom de source de données (DSN). Pour plus d’informations, consultez « Prise en charge du nom de source de données dans `sqlcmd` et `bcp` » à la fin de cette rubrique.  
  
- -e Écrire des scripts d’entrée sur le périphérique de sortie standard (stdout).

- -E Utiliser la connexion approuvée (authentification intégrée). Pour savoir comment établir des connexions approuvées qui utilisent l’authentification intégrée à partir d’un client Linux ou macOS, consultez [Utiliser l’authentification intégrée](../../../connect/odbc/linux-mac/using-integrated-authentication.md).

- -f codepage | i:codepage[,o:codepage] | o:codepage[,i:codepage] Spécifie les pages de codes d’entrée et de sortie. Le numéro de page de codes est une valeur numérique qui spécifie une page de codes Linux installée.
(disponible depuis 17.5.1.1)

- -h *nombre_de_lignes*  Spécifier le nombre de lignes à imprimer entre les en-têtes de colonnes.  
  
- -H Spécifier un nom de station de travail.  
  
- -i *input_file*[,*input_file*[,...]] Identifier le fichier contenant un traitement d'instructions SQL ou des procédures stockées.  
  
- -I Affecter la valeur ON à l’option de connexion `SET QUOTED_IDENTIFIER`.  
  
- -k Supprimer ou remplacer des caractères de contrôle.  
  
- **-K**_application\_intent_  
Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. La seule valeur actuellement prise en charge est **ReadOnly**. Si vous ne spécifiez pas **-K**, `sqlcmd` ne prend pas en charge la connectivité à un réplica secondaire dans un groupe de disponibilité AlwaysOn. Pour plus d’informations, consultez [Prise en charge par le pilote ODBC pour Linux et macOS de la haute disponibilité et de la reprise d’activité](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
> [!NOTE]  
> L’option **-K** n’est pas prise en charge dans le CTP pour SUSE Linux. Vous pouvez toutefois spécifier le mot clé **ApplicationIntent=ReadOnly** dans un fichier DSN passé à `sqlcmd`. Pour plus d’informations, consultez « Prise en charge du nom de source de données dans `sqlcmd` et `bcp` » à la fin de cette rubrique.  
  
- -l *timeout* spécifie le nombre de secondes au terme duquel une connexion `sqlcmd` expire quand vous tentez de vous connecter à un serveur.

- -m *niveau_erreur* Déterminer les messages d’erreur envoyés à stdout.  
  
- **-M**_multisubnet\_failover_  
Spécifiez toujours **-M** en cas de connexion à l’écouteur de groupe de disponibilité d’un groupe de disponibilité [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ou d’une instance de cluster de basculement [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. **-M** accélère la détection des basculements et la connexion au serveur (actuellement) actif. Si vous ne spécifiez pas l’option **-M** , **-M** est désactivé. Pour plus d’informations sur [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)], consultez [Pilote ODBC sur Linux et macOS pour la haute disponibilité et la récupération d’urgence](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  
  
> [!NOTE]  
> L’option **-M** n’est pas prise en charge dans le CTP pour SUSE Linux. Vous pouvez toutefois spécifier le mot clé **MultiSubnetFailover=Yes** dans un fichier DSN passé à `sqlcmd`. Pour plus d’informations, consultez « Prise en charge du nom de source de données dans `sqlcmd` et `bcp` » à la fin de cette rubrique.  
  
- -N Chiffrer la connexion.  
  
- -o *fichier_sortie* Identifier le fichier qui reçoit le sortie de `sqlcmd`.  
  
- -p Imprimer des statistiques de performances pour chaque jeu de résultats.  
  
- -P Spécifier un mot de passe utilisateur.  
  
- -q *requête_ligne_de_commande* Exécute une requête au démarrage de `sqlcmd`, mais ne quitte pas au terme de l’exécution de la requête.  

- -Q *requête_ligne_de_commande* Exécuter une requête au démarrage de `sqlcmd`. `sqlcmd` s’arrête quand la requête est terminée.  

- -r Redirige les messages d’erreur vers stderr.

- -R Fait en sorte que le pilote utilise les paramètres régionaux du client pour convertir les données de devise et de date et d’heure en données caractères. Uniquement actuellement uniquement la mise en forme en_US (anglais américain).
  
- -s *caractère_séparation_colonnes*  Spécifier le caractère de séparation des colonnes.  

- -S [*protocol*:] *server*[ **,** _port_]  
Spécifier l’instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à laquelle il faudra se connecter ou, si -D est utilisé, un nom de source de données. Le pilote ODBC sur Linux et macOS impose d’utiliser -S. Il est à noter que le protocole **tcp** est le seul protocole valide.  
  
- -t *délai_expiration_requête* Spécifier le nombre de secondes accordées pour l’exécution d’une commande (ou une instruction SQL).  
  
- -u Spécifier que fichier_sortie est stocké au format Unicode, quel que soit le format de fichier_entrée.  
  
- -U *ID_connexion* Spécifier un ID de connexion utilisateur.  
  
- -V *niveau_gravité_erreur* Contrôler le niveau de gravité utilisé pour définir la variable ERRORLEVEL.  
  
- -w *largeur_colonne* Spécifier la largeur d’écran de la sortie.  
  
- -W Supprimer les espaces à droite d’une colonne.  
  
- -x Désactiver la substitution de variable.  
  
- -X Désactiver les commandes, le script de démarrage et les variables d’environnement.  
  
- -y *largeur_affichage_type_longueur_variable* Définir la variable de script `sqlcmd` `SQLCMDMAXFIXEDTYPEWIDTH`.
  
- -Y *largeur_affichage_type_longueur_fixe* Définir la variable de script `sqlcmd` `SQLCMDMAXVARTYPEWIDTH`.


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
  
- -L Répertorier les serveurs configurés localement et le nom des serveurs diffusant sur le réseau.  
  
- -v Créer une variable de script `sqlcmd` pouvant être utilisée dans un script `sqlcmd`.  
  
Vous pouvez utiliser la méthode alternative suivante : Placez les paramètres dans un même fichier, que vous pouvez ensuite ajouter à un autre fichier. Cela vous aidera à utiliser un fichier de paramètres pour remplacer les valeurs. Par exemple, créer un fichier nommé `a.sql` (le fichier de paramètres) avec le contenu suivant :
  
    :setvar ColumnName object_id  
    :setvar TableName sys.objects  
  
Ensuite, créer un fichier nommé `b.sql` avec les paramètres de remplacement :  
  
    select $(ColumnName) from $(TableName)  

En ligne de commande, combinez `a.sql` et `b.sql` en `c.sql` avec les commandes suivantes :  
  
    cat a.sql > c.sql 
  
    cat b.sql >> c.sql  
  
Exécutez `sqlcmd` et utilisez `c.sql` comme fichier d’entrée :  
  
    slqcmd -S<...> -P<..> -U<..> -I c.sql  

- -z *mot_de_passe* Modifier le mot de passe.  
  
- -Z *mot_de_passe* Modifier le mot de passe et quitter.  

## <a name="unavailable-commands"></a>Commandes non disponibles

Dans la version actuelle, les commandes suivantes ne sont pas disponibles :  
  
-   :ED  
  
-   :ServerList  
  
-   :XML  
  
## <a name="dsn-support-in-sqlcmd-and-bcp"></a>Prise en charge du nom de source de données dans sqlcmd et bcp

Vous pouvez indiquer un nom de source de données (DSN) plutôt qu’un nom de serveur dans l’option **sqlcmd** ou **bcp** `-S` (ou la commande **sqlcmd** :Connect) si vous spécifiez -D. Si vous utilisez -D, **sqlcmd** ou **bcp** se connectera au serveur spécifié dans le nom de source de données par l’option -S.  
  
Les noms de sources de données système sont stockés dans le fichier `odbc.ini` du répertoire ODBC SysConfigDir (`/etc/odbc.ini` sur les installations standard). Les noms de sources de données utilisateur sont stockés dans `.odbc.ini` dans le répertoire de base de l’utilisateur (`~/.odbc.ini`).
  
Les entrées suivantes sont prises en charge dans un nom de source de données sur Linux ou macOS :

-   **ApplicationIntent=ReadOnly**  

-   **Database=** _nom\_base_de_données_  
  
-   **Driver=ODBC Driver 11 for SQL Server** ou **Driver=ODBC Driver 13 for SQL Server**
  
-   **MultiSubnetFailover=Yes**  
  
-   **Server=** _server\_name\_or\_IP\_address_  
  
-   **Trusted_Connection=yes**|**no**  
  
Dans un nom de source de données, seule l’entrée DRIVER est nécessaire, mais pour établir une connexion à un serveur, `sqlcmd` ou `bcp` a besoin de la valeur de l’entrée SERVER.  

Si vous spécifiez la même option dans le nom de source de données et sur la ligne de commande `sqlcmd` ou `bcp`, l’option de ligne de commande remplace la valeur utilisée dans le nom de source de données. Par exemple, si le nom de source de données comporte une entrée DATABASE et que la ligne de commande `sqlcmd` inclut **-d**, la valeur passée à **-d** est utilisée. Si vous spécifiez **Trusted_Connection=yes** dans le nom de source de données, l’authentification Kerberos est utilisée et le nom d’utilisateur ( **-U**) et le mot de passe ( **-P**), s’ils sont fournis, sont ignorés.

Vous pouvez modifier les scripts qui appellent `isql` pour qu’ils utilisent `sqlcmd` en définissant l’alias suivant : `alias isql="sqlcmd -D"`.  

## <a name="see-also"></a>Voir aussi  
[Connexion avec **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md)  
 
