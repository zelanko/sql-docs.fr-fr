---
title: Connexion à sqlcmd | Microsoft Docs
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
ms.openlocfilehash: a782db89033da42ebf17ed33565ec680fafa0d04
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68005914"
---
# <a name="connecting-with-sqlcmd"></a>Connexion avec sqlcmd
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

L’utilitaire [sqlcmd](https://go.microsoft.com/fwlink/?LinkID=154481) est disponible dans [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur Linux et macOS.
  
Les commandes suivantes montrent comment utiliser l’authentification Windows (Kerberos) et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l’authentification, respectivement:
  
```  
sqlcmd -E -Sxxx.xxx.xxx.xxx  
sqlcmd -Sxxx.xxx.xxx.xxx -Uxxx -Pxxx  
```  
  
## <a name="available-options"></a>Options disponibles

Dans la version actuelle, les options suivantes sont disponibles :  
  
- -? Afficher `sqlcmd` l’utilisation.  
  
- -a Demander une taille de paquet.  
  
- -b Arrêter le traitement par lots en cas d’erreur.  
  
- -c *batch_terminator* spécifiez le terminateur de lot.  
  
- -C Faire confiance au certificat de serveur.  

- -d *nom_base_de_données* émette une `USE` instruction *nom_base_de_données* au démarrage `sqlcmd`.  

- -D Fait en sorte que la valeur passée à l’option -S de `sqlcmd` soit interprétée comme un nom de source de données (DSN). Pour plus d’informations, consultez « Prise en charge du nom de source de données dans `sqlcmd` et `bcp` » à la fin de cette rubrique.  
  
- -e Écrire des scripts d’entrée sur le périphérique de sortie standard (stdout).

- Utiliser la connexion approuvée et l’authentification intégrée. Pour plus d’informations sur la création de connexions approuvées qui utilisent l’authentification intégrée à partir d’un client Linux ou macOS, consultez [utilisation de l’authentification intégrée](../../../connect/odbc/linux-mac/using-integrated-authentication.md).

- -h *nombre_de_lignes*  Spécifier le nombre de lignes à imprimer entre les en-têtes de colonnes.  
  
- -H Spécifier un nom de station de travail.  
  
- -i *input_file*[,*input_file*[,...]] Identifier le fichier contenant un traitement d'instructions SQL ou des procédures stockées.  
  
- -J’affecte la `SET QUOTED_IDENTIFIER` valeur on à l’option de connexion.  
  
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
  
- -q *commandline_query* exécute une requête au `sqlcmd` démarrage de, mais ne se ferme pas lorsque l’exécution de la requête est terminée.  

- -Q *commandline_query* exécute une requête au `sqlcmd` démarrage de. `sqlcmd` s’arrête quand la requête est terminée.  

- -r Redirige les messages d’erreur vers stderr.

- -R Fait en sorte que le pilote utilise les paramètres régionaux du client pour convertir les données de devise et de date et d’heure en données caractères. Uniquement actuellement uniquement la mise en forme en_US (anglais américain).
  
- -s *column_separator_char* spécifiez le caractère de séparation des colonnes.  

- -S [*protocol*:] *server*[ **,** _port_]  
Spécifiez l’instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de à laquelle se connecter, ou si-D est utilisé, un nom de source de nom. Le pilote ODBC sur Linux et macOS requiert-S. Notez que **TCP** est le seul protocole valide.  
  
- -t *délai_expiration_requête* Spécifier le nombre de secondes accordées pour l’exécution d’une commande (ou une instruction SQL).  
  
- -u Spécifier que fichier_sortie est stocké au format Unicode, quel que soit le format de fichier_entrée.  
  
- -U *ID_de_connexion* spécifiez un ID de connexion de l’utilisateur.  
  
- -V *niveau_gravité_erreur* Contrôler le niveau de gravité utilisé pour définir la variable ERRORLEVEL.  
  
- -w *column_width* spécifiez la largeur d’écran pour la sortie.  
  
- -W Supprimer les espaces à droite d’une colonne.  
  
- -x Désactiver la substitution de variable.  
  
- -X Désactiver les commandes, le script de démarrage et les variables d’environnement.  
  
- -y *variable_length_type_display_width* définit la `sqlcmd` variable `SQLCMDMAXFIXEDTYPEWIDTH`de script.
  
- -Y *fixed_length_type_display_width* définit la `sqlcmd` variable `SQLCMDMAXVARTYPEWIDTH`de script.


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
  
Vous pouvez utiliser la méthode alternative suivante: Placez les paramètres dans un fichier, que vous pouvez ensuite ajouter à un autre fichier. Cela vous aidera à utiliser un fichier de paramètres pour remplacer les valeurs. Par exemple, créer un fichier nommé `a.sql` (le fichier de paramètres) avec le contenu suivant :
  
    :setvar ColumnName object_id  
    :setvar TableName sys.objects  
  
Ensuite, créer un fichier nommé `b.sql` avec les paramètres de remplacement :  
  
    select $(ColumnName) from $(TableName)  

Sur la ligne de commande, `a.sql` combinez `c.sql` et `b.sql` à à l’aide des commandes suivantes:  
  
    cat a.sql > c.sql 
  
    cat b.sql >> c.sql  
  
Exécutez `sqlcmd` et utilisez `c.sql` comme fichier d’entrée:  
  
    slqcmd -S<...> -P<..> -U<..> -I c.sql  

- -z mot de passe de modification de *mot de passe* .  
  
- -Z mot de passe de modification de *mot de passe* et quitter.  

## <a name="unavailable-commands"></a>Commandes non disponibles

Dans la version actuelle, les commandes suivantes ne sont pas disponibles :  
  
-   :ED  
  
-   :ServerList  
  
-   :XML  
  
## <a name="dsn-support-in-sqlcmd-and-bcp"></a>Prise en charge du nom de source de données dans sqlcmd et bcp

Vous pouvez spécifier un nom de source de données plutôt qu’un nom de serveur dans l’option **sqlcmd** ou **bcp** `-S` (ou la commande **sqlcmd** :Connect) si vous spécifiez -D. -D fait en sorte que **sqlcmd** ou **BCP** se connecte au serveur spécifié dans le DSN par l’option-S.  
  
Les noms de sources de fichiers `odbc.ini` système sont stockés dans le fichier dans`/etc/odbc.ini` le répertoire ODBC répertoire sysconfigdir (sur les installations standard). Les noms DSN utilisateur sont `.odbc.ini` stockés dans dans le répertoire de démarrage`~/.odbc.ini`de l’utilisateur ().
  
Les entrées suivantes sont prises en charge dans un nom de source de données sur Linux ou macOS :

-   **ApplicationIntent=ReadOnly**  

-   **Base de données =** _nom\_de la base de données_  
  
-   **Driver = pilote ODBC 11 pour SQL Server** ou **Driver = pilote odbc 13 pour SQL Server**
  
-   **MultiSubnetFailover=Yes**  
  
-   **Server=** _server\_name\_or\_IP\_address_  
  
-   **Trusted_Connection=yes**|**no**  
  
Dans un nom de source de données, seule l’entrée DRIVER est nécessaire, mais pour établir une connexion à un serveur, `sqlcmd` ou `bcp` a besoin de la valeur de l’entrée SERVER.  

Si vous spécifiez la même option dans le nom de source de données et sur la ligne de commande `sqlcmd` ou `bcp`, l’option de ligne de commande remplace la valeur utilisée dans le nom de source de données. Par exemple, si le nom de source de données comporte une entrée DATABASE et que la ligne de commande `sqlcmd` inclut **-d**, la valeur passée à **-d** est utilisée. Si vous spécifiez **Trusted_Connection=yes** dans le nom de source de données, l’authentification Kerberos est utilisée et le nom d’utilisateur ( **-U**) et le mot de passe ( **-P**), s’ils sont fournis, sont ignorés.

Vous pouvez modifier les scripts qui appellent `isql` pour qu’ils utilisent `sqlcmd` en définissant l’alias suivant : `alias isql="sqlcmd -D"`.  

## <a name="see-also"></a>Voir aussi  
[Connexion avec **bcp**](../../../connect/odbc/linux-mac/connecting-with-bcp.md)  
 
