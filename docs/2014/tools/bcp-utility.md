---
title: Utilitaire bcp | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server]
- exporting data
- row exporting [SQL Server]
- copying data [SQL Server], bcp utility
- command prompt utilities [SQL Server], bcp
- tables [SQL Server], importing data
- column importing [SQL Server]
- bcp utility [SQL Server], command options
- file exporting [SQL Server]
- bulk copy [SQL Server]
- bcp utility [SQL Server], about bcp utility
- tables [SQL Server], exporting data
- row importing [SQL Server]
- importing data, bcp utility
- file importing [SQL Server]
- column exporting [SQL Server]
ms.assetid: c0af54f5-ca4a-4995-a3a4-0ce39c30ec38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ad056a757a25b8bc1c358fd37d9073370d9ed279
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54133839"
---
# <a name="bcp-utility"></a>Utilitaire bcp
  Le **bcp** utilitaire copie en bloc des données entre une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et un fichier de données dans un format spécifié par l’utilisateur. L’utilitaire **bcp** permet d’importer un grand nombre de nouvelles lignes dans des tables [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou d’exporter des données de tables dans des fichiers de données. Sauf lorsqu’il est utilisé avec l’option **queryout** , l’utilitaire ne nécessite aucune connaissance de [!INCLUDE[tsql](../includes/tsql-md.md)]. Pour importer des données dans une table, vous devez utiliser un fichier de format créé pour cette table ou comprendre la structure de la table et les types de données valides pour ses colonnes.  
  
 ![Icône de lien vers une rubrique](../../2014/database-engine/media/topic-link.gif "Icône de lien vers une rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées pour **bcp**, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
> [!NOTE]  
>  Si vous utilisez **bcp** pour sauvegarder vos données, créez un fichier de format pour enregistrer le format de données. Les fichiers de données**bcp** n’incluent pas de schéma ni d’informations de format, ce qui fait que si une table ou une vue est supprimée et si vous n’avez pas de fichier de format, il se peut que vous ne soyez pas en mesure d’importer les données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   bcp [database_name.] schema.{table_name | view_name | "query" {indata_file | outdata_file | queryoutdata_file | format nul}  
  
[-apacket_size]  
[-bbatch_size]  
[-c]  
[-C { ACP | OEM | RAW | code_page } ]  
[-ddatabase_name]  
[-eerr_file]  
[-E]  
[-fformat_file]  
[-Ffirst_row]  
[-h"hint [,...n]"]   
[-iinput_file]  
[-k]  
[-Kapplication_intent]  
[-Llast_row]  
[-mmax_errors]  
[-n]  
[-N]  
[-ooutput_file]  
[-Ppassword]  
[-q]  
[-rrow_term]  
[-R]  
[-S [server_name[\instance_name]]  
[-tfield_term]  
[-T]  
[-Ulogin_id]  
[-v]  
[-V (80 | 90 | 100 | 110)]  
[-w]  
[-x]  
/?  
```  
  
## <a name="arguments"></a>Arguments  
 *data_file*  
 Chemin d'accès complet du fichier de données. Lors de l'importation en bloc de données vers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le fichier de données contient les données à copier dans la table ou vue spécifiée. Lors de l'exportation en bloc de données à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le fichier de données contient les données provenant de la table ou vue. Le chemin d'accès peut compter entre 1 et 255 caractères. Le fichier de données peut contenir jusqu’à 2<sup>63</sup> - 1 lignes.  
  
 *database_name*  
 Nom de la base de données qui contient la table ou la vue spécifiée. Sans autre indication, il s'agit de la base de données par défaut de l'utilisateur.  
  
 Vous pouvez également spécifier explicitement le nom de la base de données avec `d-`.  
  
 **in** _data_file_ | **out**_data_file_ | **queryout**_data_file_ | **format nul**  
 Direction de la copie en bloc :  
  
-   **in** copie à partir d’un fichier dans une table ou une vue de base de données.  
  
-   **out** copie dans un fichier à partir d’une table ou d’une vue de la base de données. Si vous spécifiez un fichier existant, il est remplacé. Lors de l’extraction des données, notez que l’utilitaire **bcp** représente une chaîne vide comme une chaîne Null, et une chaîne Null comme une chaîne vide.  
  
-   **queryout** copie à partir d’une requête et doit être spécifié uniquement lors d’une copie de données en bloc à partir d’une requête.  
  
-   **format** crée un fichier de format basé sur l’option spécifiée (**- n**, `-c`, `-w`, ou **-N**) et les délimiteurs de table ou vue. Lors d’une copie en bloc de données, la commande **bcp** peut se référer à un fichier de format, ce qui permet d’éviter de ressaisir les informations de format de manière interactive. L’option **format** nécessite l’option **-f** ; la création d’un fichier de format XML nécessite aussi l’option **-x**. Pour plus d’informations, consultez [Créer un fichier de format &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md). Vous devez spécifier **nul** comme valeur (**format nul**).  
  
 *Propriétaire*  
 Nom du propriétaire de la table ou de la vue. *owner* est facultatif si l'utilisateur qui effectue l'opération est le propriétaire de la table ou de la vue. Si la valeur de *owner* n’est pas spécifiée et si l’utilisateur effectuant l’opération ne possède pas la table ou la vue spécifiée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] retourne un message d’erreur et l’opération est annulée.  
  
 **«** _query_ **»**  
 Requête [!INCLUDE[tsql](../includes/tsql-md.md)] qui retourne un jeu de résultats. Si la requête retourne plusieurs jeux de résultats, seul le premier jeu de résultats est copié dans le fichier de données ; les jeux de résultats suivants sont ignorés. Placez le nom de la requête entre guillemets doubles et tout élément imbriqué dans la requête entre guillemets simples. **queryout** doit également être spécifié uniquement lors d’une copie de données en bloc à partir d’une requête.  
  
 La requête peut référencer une procédure stockée du moment que toutes les tables référencées dans la procédure stockée existent préalablement à l'exécution de l'instruction bcp. Par exemple, si la procédure stockée génère une table temp, l’instruction **bcp** échoue parce que la table temp est uniquement disponible au moment de l’exécution du programme et pas au moment de l’exécution de l’instruction. Dans ce cas, envisagez d’insérer les résultats de la procédure stockée dans une table, puis d’utiliser **bcp** pour copier les données de la table dans un fichier de données.  
  
 *table_name*  
 Nom de la table de destination lors de l’importation de données dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**) ou nom de la table source lors de l’exportation de données à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**).  
  
 *view_name*  
 Nom de la vue de destination lors de la copie de données vers [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**in**) ou nom de la vue source lors de la copie de données à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (**out**). Seules les vues dont toutes les colonnes référencent la même table peuvent être utilisées comme vues de destination. Pour plus d’informations sur les restrictions relatives à la copie des données dans les vues, consultez [INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/insert-transact-sql).  
  
 **-a** _packet_size_  
 Spécifie le nombre d’octets, par paquet réseau, envoyés depuis/vers le serveur. Vous pouvez définir une option de configuration du serveur au moyen de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (ou de la procédure stockée système **sp_configure** ). Toutefois, la configuration du serveur peut être modifiée individuellement à l'aide de cette option. *packet_size* peut être compris entre 4 096 et 65 535 octets. Sa valeur par défaut est 4 096.  
  
 L'augmentation de la taille des paquets peut améliorer les performances des opérations de copie en bloc. S'il est demandé une taille de paquet plus importante alors que cela n'est pas possible, la valeur par défaut est utilisée. Les statistiques de performance générées par **bcp** indiquent la taille de paquet utilisée.  
  
 **-b** _batch_size_  
 Nombre de lignes par lot de données importées. Chaque lot est importé et consigné dans un journal comme transaction distincte important le lot complet avant d'être validée. Par défaut, toutes les lignes du fichier de données sont importées comme un lot. Pour distribuer les lignes entre les différents lots, spécifiez une valeur de *batch_size* inférieure au nombre de lignes du fichier de données. Si la transaction d'un lot échoue, seules les insertions du lot actif sont restaurées. Les lots dont l'importation a été effectuée par des transactions validées ne sont pas affectés par une défaillance ultérieure.  
  
 N’utilisez pas cette option conjointement avec le **-h «** ROWS_PER_BATCH  **= *`bb`*»** option.  
  
 `-c`  
 Effectue l'opération en utilisant un type de données caractères. Cette option n’affiche aucune invite pour chaque champ. Il utilise `char` comme type de stockage, avec et sans préfixes **\t** (tabulation) comme séparateur de champs et **\r\n** (caractère de saut de ligne) comme indicateur de fin de ligne. `-c` n'est pas compatible avec `-w`.  
  
 Pour plus d’informations, consultez [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md).  
  
 **-C** { **ACP** | **OEM** | **RAW** | *code_page* }  
 Indique la page de codes des données dans le fichier. *code_page* est pertinente uniquement si les données contiennent `char`, `varchar`, ou `text` colonnes avec des valeurs de caractère supérieures à 127 ou inférieures à 32.  
  
> [!NOTE]  
>  Nous recommandons de spécifier un nom de classement pour chaque colonne dans un fichier de format.  
  
|Valeur de la page de codes|Description|  
|---------------------|-----------------|  
|ACP|[!INCLUDE[vcpransi](../includes/vcpransi-md.md)]/Microsoft Windows (ISO 1252).|  
|OEM|Page de codes par défaut du client. Il s’agit de la page de codes par défaut qui est utilisée si **-C** n’est pas spécifié.|  
|RAW|Aucune conversion d'une page de codes vers une autre n'a lieu. Il s'agit de l'option la plus rapide car aucune conversion n'a lieu.|  
|*code_page*|Numéro spécifique de la page de codes, par exemple 850.<br /><br /> **&#42;&#42;Important &#42; &#42;**  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne prend pas en charge la page de codes 65001 (encodage UTF-8).|  
  
 `-d` *nom_base_de_données*  
 Spécifie la base de données à laquelle se connecter. Par défaut, bcp.exe se connecte à la base de données par défaut de l'utilisateur. Si `-d` *database_name* et un nom en trois parties (*database_name.schema.table*, passé comme premier paramètre à bcp.exe) est spécifié, une erreur se produit, car vous ne pouvez pas spécifier le nom de la base de données à deux reprises. Si *database_name* commence par un trait d’union (-) ou une barre oblique (/), n’ajoutez pas d’espace entre `-d` et le nom de la base de données.  
  
 **-e** _err_file_  
 Spécifie le chemin complet d’un fichier d’erreur utilisé pour stocker les lignes que l’utilitaire **bcp** ne peut pas transférer du fichier vers la base de données. Les messages d’erreur de la commande **bcp** sont transmis à la station de travail de l’utilisateur. Si cette option est omise, aucun fichier d'erreur n'est créé.  
  
 Si *err_file* commence par un trait d’union (-) ou une barre oblique (/), n’incluez pas d’espace entre **-e** et la valeur *err_file* .  
  
 **-E**  
 Indique que la ou les valeurs d'identité figurant dans le fichier de données importé doivent être utilisées dans la colonne d'identité. Si **-E** n’est pas spécifié, les valeurs d’identité de cette colonne figurant dans le fichier de données importé ne sont pas prises en compte et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attribue automatiquement des valeurs uniques, basées sur la valeur initiale et sur un incrément spécifié durant la création de la table.  
  
 Si le fichier de données ne contient pas de valeurs pour la colonne d'identité de la table ou de la vue, utilisez un fichier de format pour spécifier que la colonne d'identité ne doit pas être prise en compte lors de l'importation des données ; auquel cas [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attribue automatiquement des valeurs uniques à la colonne. Pour plus d’informations, consultez [DBCC CHECKIDENT &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkident-transact-sql).  
  
 L’option **-E** n’exige aucune autorisation spéciale. Pour plus d'informations, consultez la section « Notes » plus loin dans cette rubrique.  
  
 **-f** _format_file_  
 Spécifie le chemin complet au fichier de format. La signification de cette option dépend de l'environnement d'utilisation :  
  
-   Si **-f** est utilisé avec l’option **format** , le fichier de format spécifié ( *format_file* ) est créé pour la table ou la vue spécifiée. Pour créer un fichier de format XML, spécifiez également l’option **-x**. Pour plus d’informations, consultez [Créer un fichier de format &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md).  
  
-   Utilisé avec l’option **in** ou **out**, **-f** nécessite un fichier de format existant.  
  
    > [!NOTE]  
    >  L’utilisation d’un fichier de format avec l’option **in** ou **out** est facultative. En l’absence de la **-f** option, si **- n**, `-c`, `-w`, ou **-N** n’est pas spécifié, la commande vous invite à entrer des informations de format et vous permet d’enregistrer vos réponses dans un fichier de format (dont le nom par défaut est Bcp.fmt).  
  
 Si *format_file* commence par un trait d’union (-) ou une barre oblique (/), n’incluez pas d’espace entre **-f** et la valeur *format_file* .  
  
 **-F** _first_row_  
 Spécifie le numéro de la première ligne à exporter à partir d’une table ou à importer à partir d’un fichier de données. Ce paramètre nécessite une valeur supérieure à (>) 0 mais inférieure à (\<) ou égal à (=), le nombre total de lignes. En l'absence de ce paramètre, la valeur par défaut est la première ligne du fichier.  
  
 *first_row* peut être un entier positif avec une valeur maximale de 2^63-1. **-F**_first_row_ est de base 1.  
  
 **-h"** _hint_[ **,**... *n*] **"**  
 Indicateur ou indicateurs à utiliser lors de l'importation en bloc de données vers une table ou vue.  
  
 ORDER **(**_column_[ASC | DESC] [**,**...*n*]**)**  
 Ordre de tri des données dans le fichier de données. Les performances de l'importation en bloc sont améliorées si les données importées sont triées en fonction de l'index cluster de la table, le cas échéant. Si le fichier de données est trié dans un ordre différent, c'est-à-dire dans un ordre autre que celui d'une clé d'index cluster, ou s'il n'existe pas d'index cluster dans la table, l'option ORDER est ignorée. Les noms de colonnes fournis doivent être des noms de colonnes valides dans la table de destination. Par défaut, **bcp** considère que le fichier de données n’est pas ordonné. Pour une importation en bloc optimisée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] valide également le fait que les données importées sont triées.  
  
 ROWS_PER_BATCH **=**_bb_  
 Nombre de lignes de données par lot (*bb*). Utilisée quand **-b** n’est pas spécifié, cette option provoque l’envoi au serveur de la totalité du fichier de données au cours d’une transaction unique. Le serveur optimise le chargement en masse en fonction de la valeur de *bb*. Par défaut, ROWS_PER_BATCH est inconnu.  
  
 KILOBYTES_PER_BATCH **=** _cc_  
 Nombre approximatif de kilo-octets (Ko) de données par lot (*cc*). Par défaut, KILOBYTES_PER_BATCH est inconnu.  
  
 TABLOCK  
 Spécifie qu'un verrou de niveau table d'une mise à jour en bloc est obtenu pour la durée de l'opération de chargement en masse ; sinon, un verrou de niveau ligne est obtenu. Cette option augmente sensiblement les performances car le maintien d'un verrou pour la durée de la seule opération de copie réduit la contention de verrouillage de la table. Une table peut être chargée simultanément par plusieurs clients à condition qu’elle ne comporte pas d’index et que **TABLOCK** soit spécifié. Par défaut, le comportement du verrouillage est déterminé par l'option **table lock on bulk load**.  
  
 CHECK_CONSTRAINTS  
 Spécifie que toutes les contraintes sur la table ou vue cible doivent être vérifiées pendant l'opération d'importation en bloc. Sans l'option CHECK_CONSTRAINTS, toute contrainte CHECK et FOREIGN KEY est ignorée. Après l'opération, la contrainte sur la table est marquée comme non approuvée.  
  
> [!NOTE]  
>  Les contraintes UNIQUE, PRIMARY KEY et NOT NULL sont toujours appliquées.  
  
 À un point donné, vous devez vérifier les contraintes sur toute la table. Si la table n'était pas vide avant l'opération d'importation en bloc, le coût de la revalidation de la contrainte peut dépasser celui de l'application des contraintes CHECK aux données incrémentielles. Par conséquent, nous vous recommandons d'activer le contrôle de contrainte pendant une importation en bloc incrémentielle.  
  
 Il peut notamment convenir de désactiver les contraintes (comportement par défaut) si les données d'entrée contiennent des lignes qui violent des contraintes. Lorsque les contraintes CHECK sont désactivées, vous pouvez importer les données et utiliser ensuite des instructions [!INCLUDE[tsql](../includes/tsql-md.md)] pour supprimer les données non valides.  
  
> [!NOTE]  
>  **bcp** applique désormais une validation des données et des contrôles de données qui peuvent entraîner l’échec de scripts existants s’ils sont exécutés sur des données non valides dans un fichier de données.  
  
> [!NOTE]  
>  Le commutateur **-m** _max_errors_ n’applique pas le contrôle de contrainte.  
  
 FIRE_TRIGGERS  
 Spécifié avec l’argument **in**, n’importe quel déclencheur d’insertion sur la table de destination s’exécute pendant l’opération de copie en bloc. Si FIRE_TRIGGERS n'est pas spécifié, aucun déclencheur d'insertion ne s'exécute. FIRE_TRIGGERS est ignoré pour les arguments **out**, **queryout** et **format**.  
  
 **-i** _input_file_  
 Spécifie le nom d’un fichier de réponse contenant les réponses aux questions d’invite de commandes pour chaque champ de données lorsqu’une copie en bloc est effectuée en mode interactif (**- n**, `-c`, `-w`, ou **- N** sauf indication contraire).  
  
 Si *input_file* commence par un trait d’union (-) ou une barre oblique (/), n’incluez pas d’espace entre **-i** et la valeur *input_file* .  
  
 **-k**  
 Pendant l’opération, les colonnes vides doivent conserver une valeur NULL et les colonnes insérées ne doivent pas prendre de valeur par défaut. Pour plus d’informations, consultez [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md).  
  
 **-K** _application_intent_  
 Déclare le type de la charge de travail de l'application lors de la connexion à un serveur. La seule valeur possible est **ReadOnly**(lecture seule). Si **-K** n’est pas spécifié, l’utilitaire bcp ne prend pas en charge la connectivité à un réplica secondaire dans un groupe de disponibilité AlwaysOn. Pour plus d’informations, consultez [ secondaires actifs : Réplicas secondaires lisibles (groupes de disponibilité AlwaysOn)](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).  
  
 **-L** _last_row_  
 Spécifie le numéro de la dernière ligne à exporter à partir d’une table ou à importer à partir d’un fichier de données. Ce paramètre nécessite une valeur supérieure à (>) 0 mais inférieure à (\<) ou égal à (=), le numéro de la dernière ligne. En l'absence de ce paramètre, la valeur par défaut est la dernière ligne du fichier.  
  
 *last_row* peut être un entier positif avec une valeur maximale de 2^63-1.  
  
 **-m** _max_errors_  
 Spécifie le nombre maximal d’erreurs de syntaxe toléré avant l’annulation de l’opération **bcp**. Une erreur de syntaxe implique une erreur de conversion de données vers le type de données cible. Le total *max_errors* exclut les erreurs pouvant être détectées uniquement sur le serveur, telles que des violations de contrainte.  
  
 Une ligne ne pouvant pas être copiée par l’utilitaire **bcp** est ignorée et est comptabilisée comme une erreur. Si cette option est omise, sa valeur par défaut est 10.  
  
> [!NOTE]  
>  Le **-m** également ne s’applique pas à la conversion du `money` ou `bigint` des types de données.  
  
 **-n**  
 Effectue la copie en bloc en faisant appel aux types de données par défaut des données (ceux de la base de données). Cette option n'affiche aucune invite pour aucun champ, mais utilise les valeurs par défaut.  
  
 Pour plus d’informations, consultez [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md).  
  
 **-N**  
 Copie en bloc en faisant appel aux types de données natifs (base de données) des données non caractères, ainsi qu'au type Unicode pour les données caractères. Cette option, qui remplace avantageusement `-w`, sert à transférer des données d'une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers une autre à l'aide d'un fichier de données. Elle n'affiche aucune invite pour aucun champ. Utilisez-la pour transférer des données comportant des caractères ANSI étendus et conserver tous les avantages des performances du mode natif.  
  
 Pour plus d’informations, consultez [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md).  
  
 Si vous exportez, puis importer des données dans le même schéma de table à l’aide de bcp.exe avec **-N**, vous pouvez voir un avertissement de troncation s’il existe une colonne de type caractère non-Unicode, d’une longueur fixe (par exemple, `char(10)`).  
  
 Vous pouvez ignorer cet avertissement. Une façon de résoudre cet avertissement consiste à utiliser **-n** au lieu de **-N**.  
  
 **-o** _output_file_  
 Spécifie le nom d’un fichier recevant la sortie redirigée à partir de l’invite de commandes.  
  
 Si *output_file* commence par un trait d’union (-) ou une barre oblique (/), n’incluez pas d’espace entre **-o** et la valeur *output_file*.  
  
 **-p** _mot_de_passe_  
 Spécifie le mot de passe de l’ID de connexion. Si cette option n’est pas utilisée, la commande **bcp** invite à entrer un mot de passe. Si vous utilisez cette option à la fin de l’invite de commandes sans spécifier de mot de passe, **bcp** emploie le mot de passe par défaut (NULL).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../includes/ssnotestrongpass-md.md)]  
  
 Pour masquer votre mot de passe, ne spécifiez pas l’option **-P** avec l’option **-U** . À la place, après avoir spécifié **bcp** avec l’option **-U** et d’autres commutateurs (ne spécifiez pas **-P**), appuyez sur Entrée ; la commande vous demande alors d’entrer un mot de passe. Cette méthode garantit le masquage de votre mot de passe lors de son entrée.  
  
 Si *password* commence par un trait d’union (-) ou une barre oblique (/), n’ajoutez pas d’espace entre **-P** et la valeur *password* .  
  
 `-q`  
 Exécute l’instruction SET QUOTED_IDENTIFIERS ON dans la connexion entre l’utilitaire **bcp** et une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Utilisez cette option pour spécifier un nom de base de données, de propriétaire, de table ou de vue contenant un espace ou un guillemet simple. Mettez entre guillemets doubles (" ") les trois parties du nom de la table ou de la vue.  
  
 Pour spécifier un nom de base de données comportant un espace ou un guillemet simple, vous devez utiliser l’option **-q** .  
  
 `-q` ne s'applique pas aux valeurs transmises à `-d`.  
  
 Pour plus d'informations, consultez la section Notes, plus loin dans cette rubrique.  
  
 **-r** _row_term_  
 Spécifie l’indicateur de fin de ligne. Par défaut, il s’agit du caractère de saut de ligne ( **\n** ). Utilisez ce paramètre pour remplacer l'indicateur de fin de ligne par défaut. Pour plus d’informations, consultez [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).  
  
 Si vous spécifiez l'indicateur de fin de ligne en notation hexadécimale dans une commande bcp.exe, la valeur sera tronquée à 0x00. Par exemple, si vous spécifiez 0x410041, 0x41 sera utilisé.  
  
 Si *row_term* commence par un trait d’union (-) ou une barre oblique (/), n’incluez pas d’espace entre **-r** et la valeur *row_term* .  
  
 **-R**  
 Spécifie que les données de type devise, date et heure sont copiées en bloc dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] en utilisant le format régional défini par les paramètres régionaux de l'ordinateur client. Par défaut, les paramètres régionaux sont ignorés.  
  
 **-S** _server_name_[ **\\**_instance_name_]  
 Spécifie l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à laquelle établir une connexion. Si aucun serveur n’est spécifié, l’utilitaire **bcp** se connecte à l’instance par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l’ordinateur local. Cette option est requise lorsqu’une commande **bcp** est exécutée depuis un ordinateur distant sur le réseau ou sur une instance nommée locale. Pour se connecter à l’instance par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un serveur, spécifiez uniquement *server_name*. Pour vous connecter à une instance nommée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], spécifiez *server_name**_\\_** instance_name*.  
  
 `-t` *field_term*  
 Spécifie l’indicateur de fin de champ. Par défaut, il s’agit du caractère de tabulation ( **\t** ). Utilisez ce paramètre pour remplacer l'indicateur de fin de champ par défaut. Pour plus d’informations, consultez [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).  
  
 Si vous spécifiez l'indicateur de fin de champ en notation hexadécimale dans une commande bcp.exe, la valeur sera tronquée à 0x00. Par exemple, si vous spécifiez 0x410041, 0x41 sera utilisé.  
  
 Si *field_term* commence par un trait d’union (-) ou une barre oblique (/), n’incluez pas d’un espace entre `-t` et *field_term* valeur.  
  
 **-T**  
 Spécifie que l'utilitaire **bcp** se connecte à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec une connexion approuvée qui utilise la sécurité intégrée. Les informations d’identification de sécurité de l’utilisateur réseau, *login_id*et *password* , ne sont pas requises. Si **-T** n’est pas spécifié, vous devez indiquer **-U** et **-P** pour vous connecter.  
  
 **-U** _ID_connexion_  
 Spécifie l'ID de connexion utilisé pour une connexion à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Quand l’utilitaire **bcp** se connecte à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] via une connexion approuvée utilisant la sécurité intégrée, utilisez l’option **-T** (connexion approuvée) à la place de la combinaison *user name* et *password* .  
  
 **-v**  
 Indique le numéro de version et le copyright de l’utilitaire **bcp** .  
  
 **-V** (**80** | **90** | **100**| **110**)  
 Copie en bloc en faisant appel aux types de données d'une version antérieure de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Cette option ne pose aucune question pour aucun champ, mais utilise les valeurs par défaut.  
  
 **80** = [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)]  
  
 **90** = [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]  
  
 **100** = [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] et [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]  
  
 **110 = [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]**  
  
 Par exemple, pour générer des données pour les types non pris en charge par [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], mais introduits dans les versions ultérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], utilisez l'option -V80.  
  
 Pour plus d’informations, consultez [Importer des données au format natif et caractère à partir de versions antérieures de SQL Server](../relational-databases/import-export/import-native-and-character-format-data-from-earlier-versions-of-sql-server.md).  
  
 `-w`  
 Copie en bloc en utilisant les caractères Unicode. Cette option n’affiche aucune invite pour chaque champ. Il utilise `nchar` comme type de stockage, aucun préfixe, **\t** (tabulation) comme séparateur de champs, et **\n** (caractère de saut de ligne) comme indicateur de fin de ligne. `-w` n'est pas compatible avec `-c`.  
  
 Pour plus d’informations, consultez [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md).  
  
 **-x**  
 Utilisé avec les options **format** et **-f**_format_file_, génère un fichier au format XML à la place du fichier au format non XML par défaut. L’option **-x** ne fonctionne pas lors de l’importation ou de l’exportation de données. Elle génère une erreur si elle est utilisée sans **format**  et **-f**_format_file_.  
  
## <a name="remarks"></a>Notes  
 Le **bcp** client 12.0 est installé lorsque vous installez [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] outils. Si les outils sont installés pour [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] et pour une version antérieure de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], en fonction de la valeur de la variable d’environnement PATH, vous utiliserez peut-être le client **bcp** antérieur au lieu du client **bcp** 12.0. Cette variable d'environnement définit l'ensemble de répertoires utilisés par Windows pour rechercher des fichiers exécutables. Pour savoir quelle version vous utilisez, exécutez la commande **bcp /v** à l’invite de commandes Windows. Pour plus d'informations sur la définition du chemin de commande dans la variable d'environnement PATH, consultez l'aide de Windows.  
  
 Les fichiers de format XML ne sont pris en charge que si les outils [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont installés conjointement avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client.  
  
 Pour savoir où trouver l’utilitaire **bcp** ou comment l’exécuter, et pour connaître les conventions syntaxiques des utilitaires d’invite de commandes, consultez [Référence de service d’invite de commande &#40;moteur de base de données&#41;](../tools/command-prompt-utility-reference-database-engine.md).  
  
 Pour plus d’informations sur la préparation des données en vue d’une importation ou d’une exportation en bloc, consultez [Préparer des données en vue d’une exportation ou d’une importation en bloc &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 Pour savoir à quel moment les opérations d’insertion de ligne effectuées par l’importation en bloc sont consignées dans le journal des transactions, consultez [Conditions requises pour une journalisation minimale dans l’importation en bloc](../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
## <a name="native-data-file-support"></a>Prise en charge de fichier de données natif  
 Dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], l’utilitaire **bcp** prend en charge les fichiers de données natifs compatibles avec [!INCLUDE[ssVersion2000](../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]et [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
## <a name="computed-columns-and-timestamp-columns"></a>Colonnes calculées et colonnes horodateur  
 Les valeurs dans le fichier de données en cours d'importation pour des colonnes calculées ou `timestamp` sont ignorées, et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attribue automatiquement des valeurs. Si le fichier de données ne contient pas de valeurs pour les colonnes calculées ou `timestamp` de la table, utilisez un fichier de format pour spécifier que les colonnes calculées ou `timestamp` ne doivent pas être prises en compte lors de l'importation des données ; auquel cas [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] attribue automatiquement des valeurs à la colonne.  
  
 Les colonnes calculées et `timestamp` sont copiées en bloc à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vers un fichier de données comme d'ordinaire.  
  
## <a name="specifying-identifiers-that-contain-spaces-or-quotation-marks"></a>Spécification d'identificateurs contenant des espaces ou des guillemets  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peuvent inclure des caractères tels que des espaces et des guillemets incorporés. De tels identificateurs doivent être traités de la manière suivante :  
  
-   Quand vous spécifiez, à l'invite de commandes, un identificateur ou un nom de fichier comportant un espace ou une apostrophe, mettez cet identificateur entre guillemets doubles (" ").  
  
     Par exemple, la commande `bcp out` suivante crée un fichier de données nommé `Currency Types.dat`:  
  
    ```  
    bcp AdventureWorks2012.Sales.Currency out "Currency Types.dat" -T -c  
    ```  
  
-   Pour spécifier un nom de base de données qui contient un espace ou un guillemet, vous devez utiliser le `-q` option.  
  
-   Pour les noms de propriétaires, de tables ou de vues incorporant des espaces ou des guillemets simples, vous pouvez :  
  
    -   Spécifier l'option `-q`, ou  
  
    -   Placer le nom de propriétaire, de table ou de vue entre crochets ([]), à l'intérieur des guillemets simples.  
  
## <a name="data-validation"></a>Validation des données  
 **bcp** applique désormais une validation des données et des contrôles de données qui peuvent entraîner l’échec de scripts existants s’ils sont exécutés sur des données non valides dans un fichier de données. Par exemple, **bcp** vérifie maintenant que :  
  
-   la représentation en mode natif des types de données `float` ou `real` est valide ;  
  
-   les données Unicode comportent un nombre d'octets pair.  
  
 Les types de données non valides qui pouvaient être importées dans les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] risquent de ne pas pouvoir être chargées désormais ; tandis que dans les versions précédentes, l'échec ne se produisait que lorsqu'un client tentait d'accéder aux données non valides. La validation supplémentaire réduit les risques d'incidents lors de l'interrogation des données après un chargement en masse.  
  
## <a name="bulk-exporting-or-importing-sqlxml-documents"></a>Exportation et importation en bloc de documents SQLXML  
 Pour exporter ou importer en bloc des données SQLXML, utilisez l'un des types de données ci-dessous dans votre fichier de format.  
  
|Type de données|Effet|  
|---------------|------------|  
|SQLCHAR ou SQLVARYCHAR|Les données sont envoyées dans la page de codes du client ou dans la page de codes impliquée par le classement. L'effet est le même que si vous définissiez le commutateur `-c` sans spécifier de fichier de format.|  
|SQLNCHAR ou SQLNVARCHAR|Les données sont envoyées au format Unicode. L'effet est le même que si vous définissiez le commutateur `-w` sans spécifier de fichier de format.|  
|SQLBINARY ou SQLVARYBIN|Les données sont envoyées sans être converties.|  
  
## <a name="permissions"></a>Autorisations  
 Une opération **bcpout** nécessite l’autorisation SELECT sur la table source.  
  
 Une opération **bcpin** nécessite au minimum des autorisations SELECT/INSERT sur la table cible. En outre, l'autorisation ALTER TABLE est requise si l'une des conditions suivantes est vraie :  
  
-   Les contraintes existent et l'indicateur CHECK_CONSTRAINTS n'est pas spécifié.  
  
    > [!NOTE]  
    >  La désactivation des contraintes est le comportement par défaut. Pour activer les contraintes explicitement, utilisez l’option **-h** avec l’indicateur CHECK_CONSTRAINTS.  
  
-   Les déclencheurs existent et l'indicateur FIRE_TRIGGER n'est pas spécifié.  
  
    > [!NOTE]  
    >  Par défaut, les déclencheurs ne sont pas activés. Pour activer les déclencheurs explicitement, utilisez l’option **-h** avec l’indicateur FIRE_TRIGGERS.  
  
-   Vous devez utiliser l’option **-E** pour importer des valeurs d’identité à partir d’un fichier de données.  
  
> [!NOTE]  
>  L'autorisation ALTER TABLE obligatoire sur la table cible était nouvelle dans [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]. Les scripts **bcp** qui n’appliquent pas de déclencheurs et de contrôles de contrainte risquent d’échouer si le compte d’utilisateur ne possède pas d’autorisation de table ALTER pour la table cible.  
  
## <a name="character-mode--c-and-native-mode--n-best-practices"></a>Meilleures pratiques relatives au mode caractère (-c) et au mode natif (-n)  
 Cette section contient des recommandations pour le mode caractère (-c) et le mode natif (-n).  
  
-   (Administrateur/Utilisateur) Lorsque cela est possible, utilisez le format natif (-n) pour éviter le problème de séparateur. Utilisez le format natif pour exporter et importer à l'aide de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Exportez les données à partir de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l'aide de l'option -c ou -w si les données doivent être importées dans une base de données non-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   (Administrateur) Vérifiez les données à l'aide de BCP OUT. Par exemple, lorsque vous utilisez BCP OUT, BCP IN, puis BCP OUT vérifiez que les données sont correctement exportées et que les valeurs de terminateurs ne sont pas utilisées comme parties des valeurs de données. Remplacez les terminateurs par défaut (à l'aide des options -t et -r) par des valeurs hexadécimales aléatoires afin d'éviter les conflits entre les valeurs de terminateurs et les valeurs de données.  
  
-   (Utilisateur) Utilisez un terminateur long et unique (n'importe quelle séquence d'octets ou de caractères) pour minimiser les risques de conflits avec la valeur de chaîne actuelle. Cette tâche peut être réalisée à l'aide des options -t et -r.  
  
## <a name="examples"></a>Exemples  
 Cette section contient les exemples suivants :  
  
-   A. Copie de lignes de table dans un fichier de données (avec une connexion approuvée)  
  
-   b. Copie de lignes de table dans un fichier de données (avec l'authentification en mode mixte)  
  
-   C. Copie de données depuis un fichier dans une table  
  
-   D. Copie d'une colonne spécifique dans un fichier de données  
  
-   E. Copie d'une ligne spécifique dans un fichier de données  
  
-   F. Copie de données d'une requête dans un fichier de données  
  
-   G. Création d'un fichier de format non XML  
  
-   H. Création d'un fichier de format XML  
  
-   I. Utilisation d’un fichier de format pour une importation en bloc avec **bcp**  
  
### <a name="a-copying-table-rows-into-a-data-file-with-a-trusted-connection"></a>A. Copie de lignes de table dans un fichier de données (avec une connexion approuvée)  
 L’exemple suivant illustre l’option **out** sur la table `AdventureWorks2012.Sales.Currency` . Cet exemple crée un fichier de données nommé `Currency.dat` et y copie les données de table au format caractère. Cet exemple part du principe que vous utilisez l’authentification Windows et que vous disposez d’une connexion approuvée à l’instance du serveur sur laquelle vous exécutez la commande **bcp** .  
  
 À partir d'une invite de commandes, entrez la commande suivante :  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -T -c  
```  
  
### <a name="b-copying-table-rows-into-a-data-file-with-mixed-mode-authentication"></a>b. Copie de lignes de table dans un fichier de données (avec l'authentification en mode mixte)  
 L’exemple suivant illustre l’option **out** sur la table `AdventureWorks2012.Sales.Currency` . Cet exemple crée un fichier de données nommé `Currency.dat` et y copie les données de table au format caractère.  
  
 L’exemple part du principe que vous utilisez l’authentification en mode mixte ; vous devez utiliser le commutateur **-U** pour spécifier votre ID de connexion. De même, à moins que vous vous connectiez à l’instance par défaut de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur l’ordinateur local, utilisez le commutateur **-S** pour spécifier le nom du système et, éventuellement, un nom d’instance.  
  
```  
bcp AdventureWorks2012.Sales.Currency out Currency.dat -c -U<login_id> -S<server_name\instance_name>  
```  
  
 Le système demande votre mot de passe.  
  
### <a name="c-copying-data-from-a-file-to-a-table"></a>C. Copie de données depuis un fichier dans une table  
 L’exemple suivant illustre l’option **in** en utilisant le fichier créé dans l’exemple précédent (`Currency.dat`). Cependant, cet exemple crée d'abord une copie vide de la table `AdventureWorks2012 Sales.Currency`, `Sales.Currency2`, dans laquelle les données sont copiées. Cet exemple part du principe que vous utilisez l’authentification Windows et que vous disposez d’une connexion approuvée à l’instance du serveur sur laquelle vous exécutez la commande **bcp** .  
  
 Pour créer la table vide, dans l'éditeur de requête, entrez la commande suivante :  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO AdventureWorks2012.Sales.Currency2   
FROM AdventureWorks2012.Sales.Currency WHERE 1=2;  
```  
  
 Pour copier en bloc les données caractères dans la nouvelle table, c'est-à-dire pour importer les données, entrez la commande suivante à l'invite de commandes :  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -c  
```  
  
 Pour vérifier la réussite de la commande, affichez le contenu de la table dans l'éditeur de requête et entrez :  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * FROM Sales.Currency2  
```  
  
### <a name="d-copying-a-specific-column-into-a-data-file"></a>D. Copie d'une colonne spécifique dans un fichier de données  
 Pour copier une colonne spécifique, vous pouvez utiliser l’option **queryout** . L'exemple suivant copie uniquement la colonne `Name` de la table `Sales.Currency` dans un fichier de données. Cet exemple part du principe que vous utilisez l’authentification Windows et que vous disposez d’une connexion approuvée à l’instance du serveur sur laquelle vous exécutez la commande **bcp** .  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp "SELECT Name FROM AdventureWorks.Sales.Currency" queryout Currency.Name.dat -T -c  
```  
  
### <a name="e-copying-a-specific-row-into-a-data-file"></a>E. Copie d'une ligne spécifique dans un fichier de données  
 Pour copier une ligne spécifique, vous pouvez utiliser l’option **queryout** . L’exemple suivant copie uniquement la ligne du contact nommé `Jarrod Rana` de la table `AdventureWorks2012.Person.Person` dans un fichier de données (`Jarrod Rana.dat`). Cet exemple part du principe que vous utilisez l’authentification Windows et que vous disposez d’une connexion approuvée à l’instance du serveur sur laquelle vous exécutez la commande **bcp**.  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp "SELECT * FROM AdventureWorks2012.Person.Person WHERE FirstName='Jarrod' AND LastName='Rana' "  queryout "Jarrod Rana.dat" -T -c  
```  
  
### <a name="f-copying-data-from-a-query-to-a-data-file"></a>F. Copie de données d'une requête dans un fichier de données  
 Pour copier le jeu de résultats d’une instruction [!INCLUDE[tsql](../includes/tsql-md.md)] dans un fichier de données, utilisez l’option **queryout** . L'exemple suivant copie les noms de la table `AdventureWorks2012.Person.Person` , triés en fonction du nom, puis du prénom, dans le fichier de données `Contacts.txt` . Cet exemple part du principe que vous utilisez l’authentification Windows et que vous disposez d’une connexion approuvée à l’instance du serveur sur laquelle vous exécutez la commande **bcp** .  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp "SELECT FirstName, LastName FROM AdventureWorks2012.Person.Person ORDER BY LastName, Firstname" queryout Contacts.txt -c -T  
```  
  
### <a name="g-creating-a-non-xml-format-file"></a>G. Création d'un fichier de format non XML  
 L'exemple suivant crée un fichier de format non XML nommé `Currency.fmt` pour la table `Sales.Currency` dans la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]. Cet exemple part du principe que vous utilisez l’authentification Windows et que vous disposez d’une connexion approuvée à l’instance du serveur sur laquelle vous exécutez la commande **bcp** .  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c  -f Currency.fmt  
```  
  
 Pour plus d’informations, consultez [Fichiers de format non XML &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).  
  
### <a name="h-creating-an-xml-format-file"></a>H. Création d'un fichier de format XML  
 L'exemple suivant crée un fichier de format XML nommé `Currency.xml` pour la table `Sales.Currency` dans la base de données [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] . Cet exemple part du principe que vous utilisez l’authentification Windows et que vous disposez d’une connexion approuvée à l’instance du serveur sur laquelle vous exécutez la commande **bcp** .  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp AdventureWorks2012.Sales.Currency format nul -T -c -x -f Currency.xml  
```  
  
> [!NOTE]  
>  Pour utiliser le commutateur **-x**, vous devez utiliser un client **bcp** 9.0. Pour plus d’informations sur l’utilisation du client **bcp** 9.0, consultez la section « Notes ».  
  
 Pour plus d’informations, consultez [Fichiers de format XML &#40;SQL Server&#41;](../relational-databases/import-export/xml-format-files-sql-server.md).  
  
### <a name="i-using-a-format-file-to-bulk-import-with-bcp"></a>I. Utilisation d'un fichier de format pour une importation en bloc avec bcp  
 Pour utiliser un fichier de format précédemment créé lors de l’importation de données dans une instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], utilisez le commutateur **-f** avec l’option **in**. Par exemple, la commande suivante copie en bloc le contenu d'un fichier de données, `Currency.dat`, dans une copie de la table `Sales.Currency` (`Sales.Currency2`) en utilisant le fichier de format précédemment créé (`Currency.xml`). Cet exemple part du principe que vous utilisez l’authentification Windows et que vous disposez d’une connexion approuvée à l’instance du serveur sur laquelle vous exécutez la commande **bcp** .  
  
 À l'invite de commandes Windows, entrez :  
  
```  
bcp AdventureWorks2012.Sales.Currency2 in Currency.dat -T -f Currency.xml  
```  
  
> [!NOTE]  
>  Les fichiers de format s'avèrent utiles lorsque les champs des fichiers de données diffèrent des colonnes de table ; par exemple, par leur nombre, leur ordre ou leurs types de données. Pour plus d’informations, consultez [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="additional-examples"></a>Autres exemples  
 Les rubriques suivantes contiennent des exemples de l’utilisation de **bcp**:  
  
-   [Créer un fichier de format &#40;SQL Server&#41;](../relational-databases/import-export/create-a-format-file-sql-server.md)  
  
-   [Exemples d’importation et d’exportation en bloc de documents XML &#40;SQL Server&#41;](../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Conserver des valeurs d’identité lors de l’importation de données en bloc &#40;SQL Server&#41;](../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Conserver les valeurs NULL ou utiliser la valeur par défaut lors de l’importation en bloc &#40;SQL Server&#41;](../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Spécifier des indicateurs de fin de champ et de fin de ligne &#40;SQL Server&#41;](../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [Utiliser un fichier de format pour importer des données en bloc &#40;SQL Server&#41;](../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Utiliser le format caractère pour importer ou exporter des données &#40;SQL Server&#41;](../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif pour importer ou exporter des données &#40;SQL Server&#41;](../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format caractère Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utiliser le format natif Unicode pour importer ou exporter des données &#40;SQL Server&#41;](../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Préparer des données en vue d’une exportation ou d’une importation en bloc &#40;SQL Server&#41;](../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [sp_tableoption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)   
 [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)  
  
  
