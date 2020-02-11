---
title: Propriétés de la base de données (page Options) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.options.f1
ms.assetid: a3447987-5507-4630-ac35-58821b72354d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a4420aaf7b11eccecf0b04bb67a55386215f1fc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62917083"
---
# <a name="database-properties-options-page"></a>Propriétés de la base de données (page Options)
  Utilisez cette page pour consulter ou modifier les options de la base de données sélectionnée. Pour plus d’informations sur les options disponibles dans cette page, consultez [options ALTER DATABASE SET &#40;&#41;Transact-SQL ](/sql/t-sql/statements/alter-database-transact-sql-set-options).  
  
## <a name="page-header"></a>En-tête de page  
 **Classement**  
 Spécifiez le classement de la base de données en le sélectionnant dans la liste. Pour plus d’informations, voir [Set or Change the Database Collation](../collations/set-or-change-the-database-collation.md).  
  
 **Mode de récupération**  
 Spécifiez l’un des modèles suivants pour la récupération de la base de données : **Complet**, **Journalisé en bloc**ou **Simple**. Pour plus d’informations sur les modes de récupération, consultez [Modes de récupération &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md).  
  
 **Niveau de compatibilité**  
 Spécifiez la version la plus récente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prise en charge par la base de données. Les valeurs possibles sont  **SQL Server 2014 (120)**,  **SQL Server 2012 (110)** et **SQL Server 2008 (100)**. Lorsqu'une base de données SQL Server 2005 est mise à niveau vers SQL Server 2014, le niveau de compatibilité de cette base de données passe de 90 à 100.  Le niveau de compatibilité 90 n'est pas pris en charge dans SQL Server 2014. Pour plus d’informations, consultez [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
 **Type de relation contenant-contenu**  
 Spécifiez aucun ou partiel pour indiquer s'il s'agit d'une base de données autonome. Pour plus d'informations sur les bases de données autonomes, consultez [Bases de données autonomes](contained-databases.md). La propriété de serveur **Activer les bases de données autonomes** doit être définie sur **TRUE** pour qu'une base de données puisse être configurée comme étant autonome.  
  
> [!IMPORTANT]  
>  L'activation de bases de données autonomes partielle transfère le contrôle de l'accès à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux propriétaires de la base de données. Pour plus d'informations, consultez [Meilleures pratiques de sécurité recommandées avec les bases de données autonomes](security-best-practices-with-contained-databases.md).  
  
## <a name="automatic"></a>Automatique  
 **Fermeture automatique**  
 Spécifiez si la base de données doit être fermée proprement et doit libérer des ressources lorsque le dernier utilisateur ferme sa session. Les valeurs possibles sont `True` et `False`. Si la valeur de cette option est `True`, la base de données est arrêtée proprement et ses ressources sont libérées dès que le dernier utilisateur s'est déconnecté.  
  
 Création automatique des statistiques incrémentielles  
 Spécifiez si utiliser l'option incrémentielle lorsque les statistiques par partition sont créées. Pour plus d’informations sur les statistiques incrémentielles, consultez [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Créer automatiquement les statistiques**  
 Spécifiez si la base de données doit automatiquement créer les statistiques d'optimisation manquantes. Les valeurs possibles sont `True` et `False`. Si la valeur de cette option est `True`, les statistiques manquantes, requises par une requête pour l'optimisation, sont créées automatiquement durant l'optimisation. Pour plus d’informations, consultez [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **réduction automatique**  
 Spécifiez si les fichiers de base de données peuvent faire l'objet d'une réduction de taille périodique. Les valeurs possibles sont `True` et `False`. Pour plus d’informations, voir [Shrink a Database](shrink-a-database.md).  
  
 **Mise à jour automatique des statistiques**  
 Spécifiez si la base de données doit automatiquement mettre à jour les statistiques d'optimisation obsolètes. Les valeurs possibles sont `True` et `False`. Si la valeur de cette option est `True`, les statistiques non mises à jour, requises par une requête pour l'optimisation, sont créées automatiquement durant l'optimisation. Pour plus d’informations, consultez [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Mise à jour automatique des statistiques de manière asynchrone**  
 Lorsque `True`la valeur est, les requêtes qui lancent une mise à jour automatique des statistiques obsolètes n’attendent pas la mise à jour des statistiques avant la compilation. Les requêtes suivantes utiliseront les statistiques mises à jour une fois celles-ci disponibles.  
  
 Lorsque `False`, les requêtes qui initialisent une mise à jour automatique des statistiques obsolètes, attendent que les statistiques mises à jour puissent être utilisées dans le plan d’optimisation des requêtes.  
  
 L’affectation de `True` la valeur à cette option n’a aucun effet, sauf si la **mise à jour automatique des statistiques** est également définie sur. `True`  
  
## <a name="containment"></a>Relation contenant-contenu  
 Dans les bases de données autonomes, certains paramètres généralement configurés au niveau serveur peuvent l'être au niveau de la base de données.  
  
 **LCID de langue de texte intégral par défaut**  
 Spécifie une langue par défaut pour les colonnes de texte intégral indexées. L'analyse linguistique des données de texte intégral indexées dépend de la langue des données. La valeur par défaut de cette option est la langue du serveur. Pour connaître le langue correspondant au paramètre affiché, consultez [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
 **Langue par défaut**  
 Spécifie la langue par défaut pour tous les nouveaux utilisateurs de base de données autonome, sauf indication contraire.  
  
 **Déclencheurs imbriqués activés**  
 Autorise des déclencheurs à en activer d'autres. Les déclencheurs peuvent compter jusqu'à 32 niveaux d'imbrication. Pour plus d’informations, consultez la section « Déclencheurs imbriqués » de [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
 **Transformer les mots parasites**  
 Supprimez un message d'erreur si des mots parasites, ou des mots vides, provoquent le retour de lignes nulles par une opération booléenne sur une requête de texte intégral. Pour plus d’informations, voir [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md).  
  
 **Année de coupure à deux chiffres**  
 Indique le numéro d'année le plus élevé qui peut être entré en tant qu'année à deux chiffres. L'année répertoriée et les 99 années précédentes peuvent être entrées sous forme d'années à deux chiffres. Toutes les autres années doivent être entrées sous forme d'années à quatre chiffres.  
  
 Par exemple, le paramètre par défaut 2049 indique qu'une date entrée sous la forme "14/3/49" sera interprétée comme le 14 mars 2049, tandis qu'une date entrée sous la forme "14/3/50" sera interprétée comme le 14 mars 1950. Pour plus d’informations, voir [Configurer l'option de configuration de serveur two digit year cutoff](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md).  
  
## <a name="cursor"></a>Curseur  
 **Fermer le curseur lors de la validation activée**  
 Spécifiez si les curseurs doivent être fermés une fois que la transaction qui a ouvert le curseur est validée. Les valeurs possibles sont `True` et `False`. Si la valeur de cette option est `True`, tout curseur ouvert au moment où une transaction est validée ou restaurée est fermé. Si la valeur est `False`, ces curseurs restent ouverts lorsqu'une transaction est validée, Lorsque `False`, la restauration d’une transaction ferme tous les curseurs, à l’exception de ceux définis comme étant non sensibles ou statiques. Pour plus d’informations, consultez [SET CURSOR_CLOSE_ON_COMMIT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-cursor-close-on-commit-transact-sql).  
  
 **Curseur par défaut**  
 Spécifiez le comportement du curseur par défaut. Si la valeur de cette option est `True`, les déclarations de curseur ont pour valeur par défaut LOCAL. Lorsque `False`la [!INCLUDE[tsql](../../includes/tsql-md.md)] valeur est, les curseurs sont globaux par défaut.  
  
## <a name="filestream"></a>FILESTREAM  
 **Nom du répertoire FILESTREAM**  
 Spécifiez le nom de répertoire pour les données FILESTREAM associées à la base de données sélectionnée.  
  
 **Accès non transactionnel FILESTREAM**  
 Spécifiez l’une des options suivantes pour l’accès non transactionnel via le système de fichiers aux données FILESTREAM stockées dans les FileTables : **OFF**, **READ_ONLY**ou **FULL**. Si FILESTREAM n'est pas activé sur le serveur, cette valeur est définie sur OFF et est désactivée. Pour plus d’informations, consultez [FileTables &#40;SQL Server&#41;](../blob/filetables-sql-server.md).  
  
## <a name="miscellaneous"></a>Divers  
 **Valeur par défaut ANSI NULL**  
 Autorise les valeurs NULL pour tous les types de données définis par l'utilisateur ou les colonnes non explicitement définies comme `NOT NULL` au cours d'une instruction `CREATE TABLE` ou `ALTER TABLE` (l'état par défaut). Pour plus d’informations, consultez [SET ANSI_NULL_DFLT_ON &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-null-dflt-on-transact-sql) et [SET ANSI_NULL_DFLT_OFF &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-null-dflt-off-transact-sql).  
  
 **Valeurs ANSI NULL activées**  
 Spécifiez le comportement des opérateurs de comparaison Égal à (`=`) et Différent de (`<>`) lorsqu'ils sont utilisés avec des valeurs NULL. Les valeurs possibles `True` sont (on) `False` et (OFF). Si la valeur de cette option est `True`, toutes les comparaisons à une valeur NULL sont évaluées à inconnu (UNKNOWN). Lorsque `False`la valeur est, les comparaisons de valeurs non-Unicode à une `True` valeur NULL sont évaluées à si les deux valeurs sont null. Pour plus d’informations, consultez [SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql).  
  
 **Remplissage ANSI activé**  
 Spécifiez si le remplissage ANSI est activé ou désactivé. Les valeurs autorisées `True` sont (on) `False` et (OFF). Pour plus d’informations, consultez [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **Avertissements ANSI activés**  
 Spécifiez le comportement compatible avec la norme ISO de plusieurs conditions d'erreur. Lorsque `True`la valeur est, un message d’avertissement est généré si des valeurs Null apparaissent dans des fonctions d’agrégation (telles que SUM, AVG, Max, min, STDEV, STDEVP, var, VARP ou Count). Lorsque `False`la, aucun avertissement n’est émis. Pour plus d’informations, consultez [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql).  
  
 **Annulation arithmétique activée**  
 Spécifiez si l'option d'annulation arithmétique est activée ou non pour la base de données. Les valeurs possibles sont `True` et `False`. Si la valeur de cette option est `True`, un dépassement de capacité ou une division par zéro provoquent l'arrêt du traitement de la requête ou du lot d'instructions. Si l'erreur se produit dans une transaction, cette dernière est restaurée. Si la valeur de cette option est `False`, un message d'avertissement s'affiche, mais le traitement de la requête, du lot d'instructions ou de la transaction se poursuit, comme s'il n'y avait pas d'erreur. Pour plus d’informations, consultez [SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql).  
  
 **La concaténation de la valeur null donne NULL**  
 Spécifiez le comportement lorsque les valeurs NULL sont concaténées. Lorsque la valeur de la `True`propriété `string` est, + null retourne null. Lorsque `False`la valeur est, `string`le résultat est. Pour plus d’informations, consultez [SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql).  
  
 **Chaînage des propriétés des bases de données croisées activé**  
 Cette valeur en lecture seule indique si le chaînage des propriétés des bases de données croisées a été activé. Lorsque `True`la propriété est, la base de données peut être la source ou la cible d’une chaîne de propriétés de bases de données croisées. Utilisez l'instruction ALTER DATABASE pour définir cette propriété.  
  
 **Optimisation de la corrélation des dates activée**  
 Lorsque `True`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conserve les statistiques de corrélation entre deux tables quelconques de la base de données qui sont liées par une `datetime` contrainte de clé étrangère et qui ont des colonnes.  
  
 Lorsque `False`, les statistiques de corrélation ne sont pas conservées.  
  
 **Abandon d’arrondi numérique**  
 Spécifiez comment la base de données gère les erreurs d'arrondi. Les valeurs possibles sont `True` et `False`. Si la valeur de cette option est `True`, une erreur est générée lorsqu'une perte de précision survient dans une expression. Lorsque `False`la valeur est, les pertes de précision ne génèrent pas de messages d’erreur et le résultat est arrondi à la précision de la colonne ou de la variable stockant le résultat. Pour plus d’informations, consultez [SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql).  
  
 **Paramétrage**  
 Si **SIMPLE**est spécifié, les requêtes sont paramétrables en fonction du comportement par défaut de la base de données. Quand elle est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **forcée**, paramètre toutes les requêtes de la base de données.  
  
 **Identificateurs entre guillemets activés**  
 Spécifiez si les mots clés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent servir d'identificateurs (nom d'objet ou de variable) s'ils sont entre guillemets. Les valeurs possibles sont `True` et `False`. Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql).  
  
 **Déclencheurs récursifs activés**  
 Spécifiez si les déclencheurs peuvent être activés par d'autres déclencheurs. Les valeurs possibles sont `True` et `False`. Lorsque la valeur `True`est, cela active le déclenchement récursif de déclencheurs. Lorsque la valeur `False`est, seule la récursivité directe est bloquée. Pour désactiver la récurrence indirecte, affectez la valeur 0 à l'option de serveur déclencheurs imbriqués à l'aide de sp_configure. Pour plus d’informations, consultez [Créer des déclencheurs imbriqués](../triggers/create-nested-triggers.md).  
  
 `Trustworthy`  
 Lors de `True`l’affichage, cette option en lecture seule [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indique que autorise l’accès aux ressources situées en dehors de la base de données dans un contexte d’emprunt d’identité établi dans la base de données. Les contextes d'emprunt d'identité peuvent être établis dans la base de données à l'aide de l'instruction EXECUTE AS ou de l'une des clauses EXECUTE AS des modules de base de données.  
  
 Pour profiter de l'accès, le propriétaire de la base de données doit également bénéficier de l'autorisation AUTHENTICATE SERVER au niveau du serveur.  
  
 Cette propriété autorise également la création et l'exécution d'assemblys d'accès non sécurisés et externes dans la base de données. Il ne suffit pas d'affecter la valeur `True` à cette propriété ; le propriétaire de la base de données doit également avoir l'autorisation EXTERNAL ACCESS ASSEMBLY ou UNSAFE ASSEMBLY au niveau du serveur.  
  
 Par défaut, toutes les bases de données utilisateur et toutes les bases de données système (à l’exception de **msdb**) ont `False`cette propriété définie sur. La valeur ne peut pas être modifiée pour les bases de données **Model** et **tempdb** .  
  
 TRUSTWORTHY a la valeur `False` dès qu'une base de données est attachée au serveur.  
  
 La stratégie recommandée pour accéder aux ressources situées en dehors de la base de données dans un contexte d'emprunt d'identité consiste à utiliser les certificats et les signatures tels qu'ils sont apposés à l'option `Trustworthy`.  
  
 Pour définir cette propriété, utilisez l'instruction ALTER DATABASE.  
  
 **Format de stockage VarDecimal activé**  
 Cette option est en lecture seule à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] partir de et versions ultérieures, toutes les bases de données sont activées pour le format de stockage vardecimal. Cette option utilise [sp_db_vardecimal_storage_format](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql).  
  
## <a name="recovery"></a>Récupération  
 **Vérification de page**  
 Spécifiez l'option utilisée pour détecter et signaler les transactions d'E/S incomplètes à cause d'erreurs d'E/S de disque. Les valeurs possibles sont **None**, **TornPageDetection**et **Checksum**. Pour plus d’informations, consultez [Gérer la table suspect_pages &#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md).  
  
 **Temps de récupération cible (secondes)**  
 Spécifie la durée maximale (en secondes) de la récupération de la base de données spécifiée en cas d'incident. Pour plus d’informations, consultez [Points de contrôle de base de données &#40;SQL Server&#41;](../logs/database-checkpoints-sql-server.md).  
  
## <a name="state"></a>State  
 **Base de données en lecture seule**  
 Spécifiez si la base de données est en lecture seule. Les valeurs possibles sont `True` et `False`. Si la valeur de cette option est `True`, les utilisateurs sont uniquement autorisés à lire les données de la base de données. Ils ne peuvent pas modifier les données ou les objets de la base de données. Toutefois, la base de données elle-même peut être supprimée à l'aide de l'instruction DROP DATABASE. La modification de la configuration de l'option **Base de données en lecture seule** n'est possible que si la base de données n'est pas en cours d'utilisation. La base de données master est l'exception à la règle mais seul l'administrateur système peut utiliser la base de données master pendant la configuration de cette option.  
  
 **État de la base de données**  
 Affiche l'état actuel de la base de données. Elle n’est pas modifiable. Pour plus d'informations sur l'option **État de la base de données**, consultez [Database States](database-states.md).  
  
 **Restreindre l’accès**  
 Spécifiez les utilisateurs autorisés à accéder à la base de données. Les valeurs possibles sont :  
  
-   **Multiple**  
  
     État standard d'une base de données de production qui permet à plusieurs utilisateurs d'accéder en même temps à la base de données.  
  
-   **Unique**  
  
     État utilisé pour les actions de maintenance qui permet à un seul utilisateur à la fois d'accéder à la base de données.  
  
-   **Restricted (Restreint)**  
  
     Seuls les membres des rôles db_owner, dbcreator ou sysadmin peuvent utiliser la base de données.  
  
 **Chiffrement activé**  
 Dans `True`ce cas, cette base de données est activée pour le chiffrement de la base de données. Une clé de chiffrement de base de données est alors requise pour effectuer le chiffrement. Pour plus d’informations, consultez [Transparent Data Encryption &#40;TDE&#41;](../security/encryption/transparent-data-encryption.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
