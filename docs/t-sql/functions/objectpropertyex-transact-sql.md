---
title: OBJECTPROPERTYEX (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECTPROPERTYEX
- OBJECTPROPERTYEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- displaying schema-scoped object information
- viewing schema-scoped object information
- OBJECTPROPERTYEX function
- schema-scoped objects [SQL Server]
- objects [SQL Server], schema-scoped
ms.assetid: be36b3e3-3309-4332-bfb5-c7e9cf8dc8bd
caps.latest.revision: 76
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 73e4cbb26ea46753a79b9089acaaab7fe5d50e65
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="objectpropertyex-transact-sql"></a>OBJECTPROPERTYEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne des informations concernant les objets étendus aux schémas dans la base de données actuelle. Pour obtenir la liste de ces objets, consultez [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md). OBJECTPROPERTYEX ne peut pas être utilisé pour des objets qui ne sont pas étendus aux schémas, tels que les déclencheurs DDL (Data Definition Language) et les notifications d'événements.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
OBJECTPROPERTYEX ( id , property )  
```  
  
## <a name="arguments"></a>Arguments  
 *id*  
 Expression représentant l'ID de l'objet dans la base de données active. *ID* est **int** et est supposé pour être un objet de portée schéma dans le contexte actuel de la base de données.  
  
 *propriété*  
 Expression contenant les informations à retourner pour l'objet spécifié par id. Le type de retour est **sql_variant**. Le tableau qui suit indique le type de données de base pour chaque valeur de propriété.  
  
> [!NOTE]  
>  Sauf indication contraire, NULL est retourné lorsque *propriété* n’est pas un nom de propriété valide, *id* n’est pas un ID d’objet valide, *id* est un type d’objet non pris en charge pour le texte spécifié *propriété*, ou l’appelant n’a pas l’autorisation d’afficher les métadonnées de l’objet.  
  
|Nom de la propriété|Type d'objet|Description et valeurs retournées|  
|-------------------|-----------------|-------------------------------------|  
|BaseType|Tout objet étendu aux schémas|Identifie le type de base de l'objet. Lorsque l'objet spécifié est un SYNONYM, le type de base de l'objet sous-jacent est retourné.<br /><br /> Nonnull = Type d'objet<br /><br /> Type de données de base : **char(2)**|  
|CnstIsClustKey|Contrainte|Contrainte PRIMARY KEY avec un index cluster.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|CnstIsColumn|Contrainte|Contrainte CHECK, DEFAULT ou FOREIGN KEY sur une seule colonne.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|CnstIsDeleteCascade|Contrainte|Contrainte FOREIGN KEY avec l'option ON DELETE CASCADE.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|CnstIsDisabled|Contrainte|Contrainte désactivée.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|CnstIsNonclustKey|Contrainte|Contrainte PRIMARY KEY avec un index non cluster.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|CnstIsNotRepl|Contrainte|La contrainte est définie avec les mots clés NOT FOR REPLICATION.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|CnstIsNotTrusted|Contrainte|La contrainte a été activée sans vérification des lignes existantes. Il se peut donc qu'elle ne s'applique pas à toutes les lignes.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|CnstIsUpdateCascade|Contrainte|Contrainte FOREIGN KEY avec l'option ON UPDATE CASCADE.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsAfterTrigger|Déclencheur|Déclencheur AFTER.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsAnsiNullsOn|Fonction [!INCLUDE[tsql](../../includes/tsql-md.md)], procédure [!INCLUDE[tsql](../../includes/tsql-md.md)], déclencheur [!INCLUDE[tsql](../../includes/tsql-md.md)], vue|Définition des valeurs ANSI NULL lors de la création.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsDeleteTrigger|Déclencheur|Le déclencheur de suppression.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsFirstDeleteTrigger|Déclencheur|Premier déclencheur exécuté lorsqu'une instruction DELETE est exécutée sur la table.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsFirstInsertTrigger|Déclencheur|Premier déclencheur exécuté lorsqu'une instruction INSERT est exécutée sur la table.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsFirstUpdateTrigger|Déclencheur|Premier déclencheur exécuté lorsqu'une instruction UPDATE est exécutée sur la table.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsInsertTrigger|Déclencheur|Le déclencheur d’insertion.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsInsteadOfTrigger|Déclencheur|Déclencheur INSTEAD OF.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsLastDeleteTrigger|Déclencheur|Dernier déclencheur activé lorsqu'une instruction DELETE est exécutée sur la table.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsLastInsertTrigger|Déclencheur|Dernier déclencheur activé lorsqu'une instruction INSERT est exécutée sur la table.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsLastUpdateTrigger|Déclencheur|Dernier déclencheur activé lorsqu'une instruction UPDATE est exécutée sur la table.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsQuotedIdentOn|Fonction [!INCLUDE[tsql](../../includes/tsql-md.md)], procédure [!INCLUDE[tsql](../../includes/tsql-md.md)], déclencheur [!INCLUDE[tsql](../../includes/tsql-md.md)], vue|Définition de QUOTED_IDENTIFIER lors de la création.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsStartup|Procédure|Procédure de démarrage.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsTriggerDisabled|Déclencheur|Déclencheur désactivé.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsTriggerNotForRepl|Déclencheur|Déclencheur défini comme NOT FOR REPLICATION.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsUpdateTrigger|Déclencheur|Déclencheur de mise à jour.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|ExecIsWithNativeCompilation|Procédure [!INCLUDE[tsql](../../includes/tsql-md.md)]|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Procédure compilée en mode natif.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|HasAfterTrigger|Table, vue|La table ou la vue comporte un déclencheur AFTER.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|HasDeleteTrigger|Table, vue|La table ou la vue comporte un déclencheur DELETE.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|HasInsertTrigger|Table, vue|La table ou la vue comporte un déclencheur INSERT.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|HasInsteadOfTrigger|Table, vue|La table ou la vue comporte un déclencheur INSTEAD OF.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|HasUpdateTrigger|Table, vue|La table ou la vue comporte un déclencheur UPDATE.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsAnsiNullsOn|Fonction [!INCLUDE[tsql](../../includes/tsql-md.md)], procédure [!INCLUDE[tsql](../../includes/tsql-md.md)], table, déclencheur [!INCLUDE[tsql](../../includes/tsql-md.md)], vue|Spécifie que l'option ANSI NULLS de la table a la valeur ON. Toutes les comparaisons avec une valeur Null produisent la valeur UNKNOWN. Ce paramètre s'applique à l'ensemble des expressions dans la définition de la table, y compris les contraintes et les colonnes calculées, aussi longtemps que la table existe.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsCheckCnst|Tout objet étendu aux schémas|Contrainte de validation.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsConstraint|Tout objet étendu aux schémas|Contrainte.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsDefault|Tout objet étendu aux schémas|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Valeur par défaut associée.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsDefaultCnst|Tout objet étendu aux schémas|Contrainte DEFAULT.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsDeterministic|Fonctions scalaires et fonctions table, vue|Propriété de déterminisme de la fonction ou de la vue.<br /><br /> 1 = Déterministe<br /><br /> 0 = Non déterministe<br /><br /> Type de données de base : **int**|  
|IsEncrypted|Fonction [!INCLUDE[tsql](../../includes/tsql-md.md)], procédure [!INCLUDE[tsql](../../includes/tsql-md.md)], table, déclencheur [!INCLUDE[tsql](../../includes/tsql-md.md)], vue|Indique que le texte d'origine provenant de l'instruction du module a été converti dans un format d'obfuscation. La sortie générée par l'obfuscation n'est pas visible directement dans les affichages catalogue de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Les utilisateurs sans accès aux tables système ou des fichiers de base de données ne peut pas récupérer le texte obscurci. Toutefois, le texte est disponible pour les utilisateurs qui peuvent accéder soit les tables système via la [port DAC](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md) ou accéder directement aux fichiers de base de données. Les utilisateurs qui peuvent associer un débogueur au processus serveur peuvent également récupérer la procédure d'origine de la mémoire au moment de l'exécution.<br /><br /> 1 = Chiffrée<br /><br /> 0 = Non chiffrée<br /><br /> Type de données de base : **int**|  
|IsExecuted|Tout objet étendu aux schémas|Spécifie quel objet peut être exécuté (vue, procédure, fonction ou déclencheur).<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsExtendedProc|Tout objet étendu aux schémas|Procédure étendue.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsForeignKey|Tout objet étendu aux schémas|Contrainte FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsIndexed|Table, vue|Une table ou une vue avec un index.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsIndexable|Table, vue|Table ou vue dans laquelle un index peut être créé.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsInlineFunction|Fonction|Fonction Inline.<br /><br /> 1 = Fonction Inline<br /><br /> 0 = Fonction non Inline<br /><br /> Type de données de base : **int**|  
|IsMSShipped|Tout objet étendu aux schémas|Un objet créé pendant l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsPrecise|Colonne calculée, fonction, type défini par l'utilisateur, vue|Indique si l'objet contient un calcul imprécis, tel que des opérations en virgule flottante.<br /><br /> 1 = Précis<br /><br /> 0 = Imprécis<br /><br /> Type de données de base : **int**|  
|IsPrimaryKey|Tout objet étendu aux schémas|Contrainte PRIMARY KEY.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsProcedure|Tout objet étendu aux schémas|Procédure.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsQuotedIdentOn|Contrainte CHECK, définition DEFAULT, fonction [!INCLUDE[tsql](../../includes/tsql-md.md)], procédure [!INCLUDE[tsql](../../includes/tsql-md.md)], table, déclencheur [!INCLUDE[tsql](../../includes/tsql-md.md)], vue|Spécifie que le paramètre d'identificateur entre guillemets de l'objet a la valeur ON. Les guillemets doubles délimitent les identificateurs dans toutes les expressions impliquées dans la définition de l'objet.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsQueue|Tout objet étendu aux schémas|File d'attente Service Broker<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsReplProc|Tout objet étendu aux schémas|Procédure de réplication.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsRule|Tout objet étendu aux schémas|Règle liée.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsScalarFunction|Fonction|Fonction scalaire.<br /><br /> 1 = Fonction scalaire<br /><br /> 0 = Fonction non scalaire<br /><br /> Type de données de base : **int**|  
|IsSchemaBound|Fonction, Procédure, vue|Fonction ou vue liée à un schéma, créée à l'aide de SCHEMABINDING.<br /><br /> 1 = Fonction liée à un schéma<br /><br /> 0 = Fonction non liée à un schéma<br /><br /> Type de données de base : **int**|  
|IsSystemTable|Table|Table système.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsSystemVerified|Colonne calculée, fonction, type défini par l'utilisateur, vue|Les propriétés de précision et de déterminisme de l'objet peuvent être vérifiées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsTable|Table|Table.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsTableFunction|Fonction|Fonction table.<br /><br /> 1 = Fonction table<br /><br /> 0 = Fonction non-table<br /><br /> Type de données de base : **int**|  
|IsTrigger|Tout objet étendu aux schémas|Déclencheur.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsUniqueCnst|Tout objet étendu aux schémas|Contrainte UNIQUE.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsUserTable|Table|Table définie par l'utilisateur.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|IsView|Affichage|Vue.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|OwnerId|Tout objet étendu aux schémas|Propriétaire de l'objet.<br /><br /> **Remarque :** le propriétaire du schéma n’est pas nécessairement le propriétaire de l’objet. Par exemple, les objets enfants (ceux pour lesquels *parent_object_id* est non null) retournent toujours le même ID de propriétaire en tant que parent.<br /><br /> Nonnull = ID d'utilisateur de base de données du propriétaire de l'objet.<br /><br /> NULL = Type d'objet non pris en charge, ou ID d'objet non valide.<br /><br /> Type de données de base : **int**|  
|SchemaId|Tout objet étendu aux schémas|ID du schéma associé à l'objet.<br /><br /> Nonnull = ID de schéma de l'objet.<br /><br /> Type de données de base : **int**|  
|SystemDataAccess|Fonction, vue|L'objet accède aux données système, aux catalogues système ou aux tables système virtuelles, dans l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 0 = Aucun<br /><br /> 1 = Lecture<br /><br /> Type de données de base : **int**|  
|TableDeleteTrigger|Table|La table comporte un déclencheur DELETE.<br /><br /> > 1 = ID du premier déclencheur du type spécifié.<br /><br /> Type de données de base : **int**|  
|TableDeleteTriggerCount|Table|La table comporte le nombre de déclencheurs DELETE spécifié.<br /><br /> Nonnull = Nombre de déclencheurs DELETE<br /><br /> Type de données de base : **int**|  
|TableFullTextMergeStatus|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Indique s'il s'agit d'une table qui a un index de recherche en texte intégral qui est en cours de fusion.<br /><br /> 0 = La table n'a pas d'index de recherche en texte intégral ou l'index de recherche en texte intégral n'est pas en cours de fusion.<br /><br /> 1 = L'index de recherche en texte intégral est en cours de fusion.|  
|TableFullTextBackgroundUpdateIndexOn|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> L'index de mise à jour d'arrière-plan en texte intégral (suivi des modifications automatiques) est activé pour la table.<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> Type de données de base : **int**|  
|TableFulltextCatalogId|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> ID du catalogue de texte intégral dans lequel résident les données d'indexation de texte intégral de la table.<br /><br /> Différent de zéro = ID de catalogue de texte intégral associé à l'index unique qui identifie les lignes dans une table indexée en texte intégral.<br /><br /> 0 = Table sans index de recherche en texte intégral.<br /><br /> Type de données de base : **int**|  
|TableFullTextChangeTrackingOn|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Le suivi des modifications de texte intégral est activé pour la table.<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE<br /><br /> Type de données de base : **int**|  
|TableFulltextDocsProcessed|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre de lignes traitées depuis le démarrage de l'indexation de texte intégral. Dans une table en cours d'indexation pour une recherche en texte intégral, toutes les colonnes d'une ligne sont considérées comme faisant partie d'un même document à indexer.<br /><br /> 0 = Aucune analyse ou indexation de texte intégral active n'est terminée.<br /><br /> > 0 = une des valeurs suivantes (A ou B) : A) le nombre de documents traités par les opérations de mise à jour depuis le démarrage de complète, incrémentielle ou d’insertion ou modification manuelle de remplissage ; (B) le nombre de lignes traitées par l’insertion ou les opérations de mise à jour depuis l’activation du suivi des modifications avec remplissage de l’index de mise à jour en arrière-plan, le schéma d’index de recherche en texte intégral modifié, la reconstruction du catalogue de texte intégral ou l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] redémarré et ainsi de suite.<br /><br /> NULL = La table n'a pas d'index de recherche en texte intégral.<br /><br /> Type de données de base : **int**<br /><br /> **Remarque** cette propriété ne pas surveiller ou nombre de lignes supprimées.|  
|TableFulltextFailCount|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre de lignes que la recherche en texte intégral n'a pas indexées.<br /><br /> 0 = Le remplissage est terminé.<br /><br /> > 0 = une des valeurs suivantes (A ou B) : A) le nombre de documents qui n’ont pas été indexés depuis le démarrage complet, incrémentiel ou mise à jour manuelle du suivi des modifications population ; B) pour le suivi des modifications avec arrière-plan mettre à jour les index, le nombre de lignes qui n’ont pas été indexés depuis le début de la population, ou le redémarrage de la population. Ceci peut être provoqué par une modification du schéma, une reconstruction du catalogue, un redémarrage du serveur, etc.<br /><br /> NULL = Table sans index de recherche en texte intégral.<br /><br /> Type de données de base : **int**|  
|TableFulltextItemCount|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nonnull = Nombre de lignes qui ont été correctement indexées en texte intégral.<br /><br /> NULL = La table n'a pas d'index de recherche en texte intégral.<br /><br /> Type de données de base : **int**|  
|TableFulltextKeyColumn|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> ID de la colonne associée à l'index de colonne unique qui fait partie de la définition d'un index de recherche en texte intégral et d'un index sémantique.<br /><br /> 0 = Table sans index de recherche en texte intégral.<br /><br /> Type de données de base : **int**|  
|TableFulltextPendingChanges|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre d'entrées de suivi des modifications en attente de traitement.<br /><br /> 0 = Le suivi des modifications n'est pas activé.<br /><br /> NULL = La table n'a pas d'index de recherche en texte intégral.<br /><br /> Type de données de base : **int**|  
|TableFulltextPopulateStatus|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = Inactif.<br /><br /> 1 = Remplissage complet en cours.<br /><br /> 2 = Remplissage incrémentiel en cours.<br /><br /> 3 = Propagation des changements suivis en cours.<br /><br /> 4 = Création de l'index de mise à jour d'arrière-plan en cours, par exemple le suivi des modifications automatiques.<br /><br /> 5 = Indexation de texte intégral accélérée ou suspendue.<br /><br /> 6 = une erreur s’est produite. Examinez le journal d’analyse pour plus d’informations. Pour plus d’informations, consultez la **dépannage des erreurs dans un remplissage de texte intégral (analyse)** section de [alimenter des index de recherche en texte intégral](../../relational-databases/search/populate-full-text-indexes.md).<br /><br /> Type de données de base : **int**|  
|TableFullTextSemanticExtraction|Table|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> La table est activée pour l'indexation sémantique.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasActiveFulltextIndex|Table|**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> La table dispose d'un index de recherche en texte intégral actif.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasCheckCnst|Table|La table comporte une contrainte CHECK.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasClustIndex|Table|La table comporte un index cluster.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasDefaultCnst|Table|La table comporte une contrainte DEFAULT.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasDeleteTrigger|Table|La table comporte un déclencheur DELETE.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasForeignKey|Table|La table comporte une contrainte FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasForeignRef|Table|La table est référencée par une contrainte FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasIdentity|Table|La table comporte une colonne d'identité.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasIndex|Table|La table comporte un index de type non défini.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasInsertTrigger|Table|L'objet comporte un déclencheur INSERT.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasNonclustIndex|Table|La table comporte un index non cluster.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasPrimaryKey|Table|La table comporte une clé primaire.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasRowGuidCol|Table|Table comporte un ROWGUIDCOL pour une **uniqueidentifier** colonne.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasTextImage|Table|Table a un **texte**, **ntext**, ou **image** colonne.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasTimestamp|Table|Table a un **timestamp** colonne.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasUniqueCnst|Table|La table comporte une contrainte UNIQUE.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasUpdateTrigger|Table|La table comporte un déclencheur UPDATE.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableHasVarDecimalStorageFormat|Table|Table est activée pour **vardecimal** le format de stockage.<br /><br /> 1 = True<br /><br /> 0 = False|  
|TableInsertTrigger|Table|La table comporte un déclencheur INSERT.<br /><br /> > 1 = ID du premier déclencheur du type spécifié.<br /><br /> Type de données de base : **int**|  
|TableInsertTriggerCount|Table|La table comporte le nombre de déclencheurs INSERT spécifié.<br /><br /> >0 = Nombre de déclencheurs INSERT.<br /><br /> Type de données de base : **int**|  
|TableIsFake|Table|La table n'est pas réelle. Elle est matérialisée en interne à la demande par le [!INCLUDE[ssDE](../../includes/ssde-md.md)].<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableIsLockedOnBulkLoad|Table|La table est verrouillée, car un **bcp** ou de tâche d’insertion en bloc.<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**|  
|TableIsMemoryOptimized|Table|**S'applique à**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> La table est optimisée en mémoire<br /><br /> 1 = True<br /><br /> 0 = False<br /><br /> Type de données de base : **int**<br /><br /> Pour plus d’informations, consultez [OLTP en mémoire &#40;optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).|  
|TableIsPinned|Table|La table est épinglée pour être conservée dans le cache de données.<br /><br /> 0 = False<br /><br /> Cette fonctionnalité n'est pas prise en charge par [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures.|  
|TableTextInRowLimit|Table|Cette table comporte un jeu d'options text in row.<br /><br /> > 0 = Nombre maximal d'octets autorisé pour text in row.<br /><br /> 0 = l'option text in row n'est pas définie.<br /><br /> Type de données de base : **int**|  
|TableUpdateTrigger|Table|Table comporte un déclencheur de mise à jour.<br /><br /> > 1 = ID du premier déclencheur du type spécifié.<br /><br /> Type de données de base : **int**|  
|TableUpdateTriggerCount|Table|Table comporte le nombre de déclencheurs UPDATE spécifié.<br /><br /> > 0 = Nombre de déclencheurs UPDATE.<br /><br /> Type de données de base : **int**|  
|UserDataAccess|Fonction, vue|Indique que l'objet a accès aux données utilisateur, aux tables utilisateur, dans l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = Lecture<br /><br /> 0 = Aucun<br /><br /> Type de données de base : **int**|  
|TableHasColumnSet|Table|La table comporte un jeu de colonnes.<br /><br /> 0 = False<br /><br /> 1 = True<br /><br /> Pour plus d’informations, consultez [Utiliser des jeux de colonnes](../../relational-databases/tables/use-column-sets.md).|  
|Cardinalité|Table (système ou définie par l'utilisateur), vue ou index|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre de lignes dans l'objet spécifié.|  
|TableTemporalType|Table|**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Spécifie le type de table.<br /><br /> 0 = la table non temporelle<br /><br /> 1 = la table d’historique pour la table à système par version<br /><br /> 2 = la table temporelle avec version système|  
  
## <a name="return-types"></a>Types de retour  
 **sql_variant**  
  
## <a name="exceptions"></a>Exceptions  
 Retourne la valeur NULL en cas d'erreur ou si un appelant n'est pas autorisé à afficher l'objet.  
  
 Un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'une autorisation. Cela signifie que les fonctions intégrées générant des métadonnées, telles que OBJECTPROPERTYEX, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Notes  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] suppose que *object_id* est dans le contexte actuel de la base de données. Une requête qui fait référence à un *object_id* dans une autre base de données renverra NULL ou des résultats incorrects. Par exemple, dans la requête suivante, le contexte actuel de la base de données est la base de données master. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] essaiera de rétablir la valeur de propriété spécifié *object_id* dans cette base de données au lieu de la base de données qui est spécifié dans la requête. La requête retourne des résultats incorrects, car la vue `vEmployee` n’est pas dans la base de données master.  
  
```  
USE master;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID(N'AdventureWorks2012.HumanResources.vEmployee'), 'IsView');  
GO  
```  
  
 OBJECTPROPERTYEX (*view_i*d, 'IsIndexable') peut consommer des ressources informatiques importantes, car l’évaluation de la propriété IsIndexable nécessite l’analyse de la définition de la vue, la normalisation et son optimisation partielle. Bien que la propriété IsIndexable identifie les tables ou les vues qui peuvent être indexées, la création réelle de l'index peut malgré tout échouer si certaines conditions de clé d'index ne sont pas remplies. Pour plus d’informations, consultez [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
 OBJECTPROPERTYEX (*table_id*, 'TableHasActiveFulltextIndex') retourne la valeur 1 (true) lorsqu’au moins une colonne d’une table est ajoutée pour l’indexation. L'indexation de texte intégral est activée au niveau du remplissage dès l'ajout de la première colonne à indexer.  
  
 Des restrictions sur la visibilité des métadonnées sont appliquées à le jeu de résultats. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-finding-the-base-type-of-an-object"></a>A. Recherche du type de base d'un objet  
 L'exemple qui suit crée un SYNONYM `MyEmployeeTable` pour la table `Employee` de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], puis renvoie le type de base du SYNONYM.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE SYNONYM MyEmployeeTable FOR HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX ( object_id(N'MyEmployeeTable'), N'BaseType')AS [Base Type];  
GO  
```  
  
 Le jeu de résultats montre que le type de base de l'objet sous-jacent, la table `Employee`, est une table utilisateur.  
  
 ```
Base Type 
--------  
U
```  
  
### <a name="b-returning-a-property-value"></a>B. Renvoi d'une valeur de propriété  
 L'exemple suivant renvoie le nombre de déclencheurs UPDATE sur la table spécifiée.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID(N'HumanResources.Employee'), N'TABLEUPDATETRIGGERCOUNT');  
GO  
  
```  
  
### <a name="c-finding-tables-that-have-a-foreign-key-constraint"></a>C. Recherche de tables comportant une contrainte FOREIGN KEY  
 L'exemple suivant utilise la propriété `TableHasForeignKey` pour retourner toutes les tables comportant une contrainte FOREIGN KEY.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name, object_id, schema_id, type_desc  
FROM sys.objects   
WHERE OBJECTPROPERTYEX(object_id, N'TableHasForeignKey') = 1  
ORDER BY name;  
GO  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-finding-the-base-type-of-an-object"></a>D: recherche le type de base d’un objet  
 L’exemple suivant retourne le type de base de `dbo.DimReseller` objet.  
  
```  
-- Uses AdventureWorks  
  
SELECT OBJECTPROPERTYEX ( object_id(N'dbo.DimReseller'), N'BaseType')AS BaseType;  
```  
  
 Le jeu de résultats montre que le type de base de l'objet sous-jacent, la table `dbo.DimReseller`, est une table utilisateur.  
  
```  
BaseType   
--------   
U   
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER un SYNONYME &#40; Transact-SQL &#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [Object_id &#40; Transact-SQL &#41;](../../t-sql/functions/object-id-transact-sql.md)   
 [Nom_objet &#40; Transact-SQL &#41;](../../t-sql/functions/object-name-transact-sql.md)   
 [Sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)  
  
  


