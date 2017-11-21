---
title: column_constraint (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- column_constraint
- column_constraint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER TABLE statement
- constraints [SQL Server], properties
- constraints [SQL Server], definitions
- column_constraint
ms.assetid: 8119b7c7-e93b-4de5-8f71-c3b7c70b993c
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4f8238266e82aadeee973772266de1c74712f28
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-table-columnconstraint-transact-sql"></a>ALTER TABLE column_constraint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Spécifie les propriétés d’une contrainte PRIMARY KEY, FOREIGN KEY, UNIQUE ou CHECK qui fait partie d’une nouvelle définition de colonne ajoutée à une table à l’aide de [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ CONSTRAINT constraint_name ]   
{   
    [ NULL | NOT NULL ]   
    { PRIMARY KEY | UNIQUE }   
        [ CLUSTERED | NONCLUSTERED ]   
        [ WITH FILLFACTOR = fillfactor ]   
        [ WITH ( index_option [, ...n ] ) ]  
        [ ON { partition_scheme_name (partition_column_name)   
            | filegroup | "default" } ]   
    | [ FOREIGN KEY ]   
        REFERENCES [ schema_name . ] referenced_table_name   
            [ ( ref_column ) ]   
        [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]   
        [ NOT FOR REPLICATION ]   
    | CHECK [ NOT FOR REPLICATION ] ( logical_expression )  
}  
```  
  
## <a name="arguments"></a>Arguments  
 CONSTRAINT  
 Spécifie le début de la définition d'une contrainte PRIMARY KEY, UNIQUE, FOREIGN KEY ou CHECK.  
  
 *constraint_name*  
 Est le nom de la contrainte. Les noms de contrainte doivent respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md), sauf que le nom ne peut pas commencer par un signe dièse (#). Si *constraint_name* est ne pas fourni, un nom généré par le système est affecté à la contrainte.  
  
 NULL | NOT NULL  
 Spécifie si la colonne accepte les valeurs NULL. Les colonnes n'autorisant pas les valeurs NULL peuvent uniquement être ajoutées si une valeur par défaut a été définie pour celles-ci. Si la nouvelle colonne accepte les valeurs NULL et qu'aucune valeur par défaut n'est spécifiée, la colonne contient une valeur NULL pour chaque ligne de la table. Si la nouvelle colonne accepte les valeurs NULL et qu'une valeur par défaut est ajoutée avec la nouvelle colonne, l'option WITH VALUES peut être utilisée pour stocker la valeur par défaut dans la nouvelle colonne pour chaque ligne existante de la table.  
  
 Si la nouvelle colonne n'accepte pas les valeurs NULL, une définition de valeur par défaut DEFAULT doit être ajoutée avec la nouvelle colonne. La nouvelle colonne est automatiquement chargée avec la valeur par défaut dans les nouvelles colonnes de chaque ligne existante.  
  
 Lorsque l'ajout d'une colonne requiert des modifications physiques des lignes de données d'une table, telles que l'ajout de valeurs DEFAULT à chaque ligne, des verrous sont placés sur la table pendant l'exécution de ALTER TABLE. Cette opération affecte la possibilité de modifier le contenu de la table pendant que le verrou est en place. En revanche, l'ajout d'une colonne qui accepte les valeurs NULL et qui ne spécifie pas de valeur par défaut est uniquement une opération de métadonnées et n'implique aucun verrou.  
  
 Lorsque vous utilisez CREATE TABLE ou ALTER TABLE, les paramètres de la base de données et de la session influencent et éventuellement modifient la possibilité de valeur NULL pour le type de données utilisé dans une définition de colonne. Il est recommandé de toujours définir de manière explicite une colonne non calculée comme NULL ou NOT NULL ou, si vous utilisez un type de données défini par l'utilisateur, que vous autorisiez la colonne à utiliser la possibilité de valeur NULL par défaut pour ce type de données. Pour plus d’informations, consultez [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md).  
  
 PRIMARY KEY  
 Est une contrainte qui applique l’intégrité d’entité pour une ou plusieurs colonnes spécifiées à l’aide d’un index unique. Une seule contrainte PRIMARY KEY peut être créée par table.  
  
 UNIQUE  
 Contrainte assurant l'intégrité de l'entité d'une colonne ou de plusieurs colonnes données au moyen d'un seul index.  
  
 CLUSTERED et NONCLUSTERED  
 Spécifie qu'un index, cluster ou non-cluster, est créé pour la contrainte PRIMARY KEY ou UNIQUE. La valeur par défaut des contraintes PRIMARY KEY est CLUSTERED. La valeur par défaut des contraintes UNIQUE est, elle, NONCLUSTERED.  
  
 Si une contrainte ou un index cluster existe déjà pour la table, vous ne pouvez pas spécifier CLUSTERED. Dans ce cas, l'option par défaut d'une contrainte PRIMARY KEY devient NONCLUSTERED.  
  
 Colonnes de la **ntext**, **texte**, **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **xml**, ou **image** des types de données ne peut pas être spécifiées comme colonnes pour un index.  
  
 FILLFACTOR  **=**  *facteur de remplissage*  
 Spécifie le remplissage par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] des pages d'index utilisées pour stocker les données d'index. Valeurs du facteur de remplissage spécifiées par l’utilisateur peuvent être comprise entre 1 et 100. Si aucune valeur n'est spécifiée, la valeur par défaut est 0.  
  
> [!IMPORTANT]  
>  Documentation WITH FILLFACTOR = *fillfactor* que la seule option d’index qui s’applique aux contraintes PRIMARY KEY ou UNIQUE est conservée pour compatibilité descendante, mais il ne sera plus indiquée ainsi dans les futures mises à jour. Autres options d’index peuvent être spécifiées dans le [index_option](../../t-sql/statements/alter-table-index-option-transact-sql.md) clause ALTER TABLE.  
  
 ON { *partition_scheme_name***(***partition_column_name***)** | *groupe de fichiers* | **»**par défaut**»** }  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie le lieu de stockage de l'index créé pour la contrainte. Si *partition_scheme_name* est spécifié, l’index est partitionné et les partitions sont mappées aux groupes de fichiers qui sont spécifiés par *partition_scheme_name*. Si *groupe de fichiers* est spécifié, l’index est créé dans le groupe de fichiers nommé. Si **»**par défaut**»** est spécifié ou si ON n’est pas du tout spécifié, l’index est créé dans le même groupe de fichiers que la table. Si l'option ON est spécifiée lors de l'ajout d'un index cluster pour une contrainte PRIMARY KEY ou UNIQUE, la table dans son intégralité est déplacée dans le groupe de fichiers spécifié lorsque l'index cluster est créé.  
  
 Dans ce contexte, « default » n'est pas un mot clé. Il est un identificateur pour le groupe de fichiers par défaut et doit être délimité, comme dans ON **»**par défaut**»** ou ON **[**par défaut**]**. Si **»**par défaut**»** est spécifié, l’option QUOTED_IDENTIFIER doit avoir la valeur ON pour la session active. Il s'agit du paramètre par défaut. Pour plus d’informations, consultez [SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](../../t-sql/statements/set-quoted-identifier-transact-sql.md).  
  
 FOREIGN KEY REFERENCES  
 Contrainte assurant l'intégrité référentielle des données d'une colonne. Une contrainte FOREIGN KEY exige que chaque valeur de la colonne existe dans la colonne spécifiée de la table référencée.  
  
 *schema_name*  
 Nom du schéma auquel appartient la table référencée par la contrainte FOREIGN KEY.  
  
 *referenced_table_name*  
 Table référencée par la contrainte FOREIGN KEY.  
  
 *colonne_de_réf*  
 Colonne entre parenthèses référencée par la nouvelle contrainte FOREIGN KEY.  
  
 LORS DE LA SUPPRESSION { **AUCUNE ACTION** | CASCADE | DÉFINIR NULL | PAR DÉFAUT DE SET}  
 Spécifie l'action qui se produit dans les lignes de la table modifiée, si ces lignes comportent une relation référentielle et que la ligne référencée est supprimée de la table parent. La valeur par défaut est NO ACTION.  
  
 NO ACTION  
 Le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] déclenche une erreur et la suppression de la ligne dans la table parent est annulée.  
  
 CASCADE  
 Les lignes correspondantes sont supprimées de la table de référence pour celles supprimées de la table parent.  
  
 SET NULL  
 Toutes les valeurs composant la clé étrangère sont définies sur NULL si la ligne correspondante se trouvant à l'origine dans la table parent est supprimée. Pour que cette contrainte s'applique, les colonnes clés étrangères doivent pouvoir cependant être définies sur NULL.  
  
 SET DEFAULT  
 Toutes les valeurs composant la clé étrangère sont définies sur leur valeur par défaut si la ligne correspondante se trouvant à l'origine dans la table parent est supprimée. Pour que cette contrainte s'applique, les colonnes clés étrangères doivent disposer cependant de valeur par défaut. Si une colonne peut être affectée de la valeur NULL et qu'aucune valeur par défaut n'est définie, NULL constitue alors la valeur par défaut de la colonne de façon implicite.  
  
 Ne spécifiez pas CASCADE si la table est incluse dans une publication de fusion qui utilise des enregistrements logiques. Pour plus d’informations sur les enregistrements logiques, consultez [Regrouper les modifications apportées à des lignes connexes à l’aide d’enregistrements logiques](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 L'action ON DELETE CASCADE ne peut pas être définie si le déclencheur ON DELETE de l'option INSTEAD OF existe déjà dans la table en cours de modification.  
  
 Par exemple, dans le [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données, le **ProductVendor** table possède une relation référentielle avec la **fournisseur** table. Le **ProductVendor.VendorID** références de clés étrangères le **Vendor.VendorID** clé primaire.  
  
 Si une instruction DELETE est exécutée sur une ligne dans le **fournisseur** table et qu’une action ON DELETE CASCADE est spécifiée pour **ProductVendor.VendorID**, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] vérifie pour une ou plusieurs lignes dépendantes dans la **ProductVendor** table. S’il en existe, les lignes dépendantes dans la **ProductVendor** table est supprimée, ainsi que la ligne référencée dans la **fournisseur** table.  
  
 À l’inverse, si NO ACTION est spécifiée, la [!INCLUDE[ssDE](../../includes/ssde-md.md)] génère une erreur et annule l’action de suppression sur le **fournisseur** ligne lorsqu’il existe au moins une ligne dans le **ProductVendor** table fait référence.  
  
 MISE À JOUR { **AUCUNE ACTION** | CASCADE | DÉFINIR NULL | PAR DÉFAUT DE SET}  
 Spécifie l'action qui se produit sur les lignes de la table modifiée, si chacune de ces lignes possède une relation référentielle et que la ligne référencée correspondante est mise à jour dans la table parent. La valeur par défaut est NO ACTION.  
  
 NO ACTION  
 Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] déclenche une erreur et la mise à jour de la ligne dans la table parente est restaurée.  
  
 CASCADE  
 Les lignes correspondantes sont mises à jour dans la table de référence si la ligne de la table parent est mise à jour.  
  
 SET NULL  
 Toutes les valeurs composant la clé étrangère sont définies sur NULL si la ligne correspondante se trouvant à l'origine dans la table parent est mise à jour. Pour que cette contrainte s'applique, les colonnes clés étrangères doivent pouvoir cependant être définies sur NULL.  
  
 SET DEFAULT  
 Toutes les valeurs composant la clé étrangère sont définies sur leur valeur par défaut si la ligne correspondante se trouvant à l'origine dans la table parent est mise à jour. Pour que cette contrainte s'applique, les colonnes clés étrangères doivent disposer cependant de valeur par défaut. Si une colonne peut être affectée de la valeur NULL et qu'aucune valeur par défaut n'est définie, NULL constitue alors la valeur par défaut de la colonne de façon implicite.  
  
 Ne spécifiez pas CASCADE si la table est incluse dans une publication de fusion qui utilise des enregistrements logiques. Pour plus d’informations sur les enregistrements logiques, consultez [Regrouper les modifications apportées à des lignes connexes à l’aide d’enregistrements logiques](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 L'action ON UPDATE CASCADE, SET NULL ou SET DEFAULT ne peut pas être définie si le déclencheur ON UPDATE de l'option INSTEAD OF existe déjà dans la table en cours de modification.  
  
 Par exemple, dans le [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] base de données, le **ProductVendor** table possède une relation référentielle avec la **fournisseur** table. Le **ProductVendor.VendorID** références de clés étrangères le **Vendor.VendorID** clé primaire.  
  
 Si une instruction UPDATE est exécutée sur une ligne dans le **fournisseur** table et qu’une action ON UPDATE CASCADE est spécifiée pour **ProductVendor.VendorID**, le [!INCLUDE[ssDE](../../includes/ssde-md.md)] vérifie pour une ou plusieurs lignes dépendantes dans la **ProductVendor** table. Si elle existe, la ligne dépendante dans la **ProductVendor** table sera mise à jour, outre la ligne référencée dans la **fournisseur** table.  
  
 À l’inverse, si NO ACTION est spécifiée, la [!INCLUDE[ssDE](../../includes/ssde-md.md)] génère une erreur et annule l’action de mise à jour de la **fournisseur** ligne lorsqu’il existe au moins une ligne dans le **ProductVendor** table fait référence.  
  
 NOT FOR REPLICATION  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Peut être indiqué aussi bien pour les contraintes FOREIGN KEY que CHECK. Si cette clause est spécifiée pour une contrainte, la contrainte n'est pas appliquée lorsque les agents de réplication effectuent des opérations d'insertion, de mise à jour ou de suppression.  
  
 CHECK  
 Contrainte qui assure l'intégrité du domaine en limitant les valeurs possibles pouvant être entrées dans une ou plusieurs colonnes.  
  
 *Logical_Expression*  
 Expression logique utilisée dans une contrainte CHECK et retournant TRUE ou FALSE. *Logical_Expression* utilisé avec la vérification de contrainte ne peut pas référencer une autre table mais peut référencer d’autres colonnes dans la même table pour la même ligne. L'expression ne peut pas faire référence à un type de données alias.  
  
## <a name="remarks"></a>Notes  
 Lorsque des contraintes CHECK ou FOREIGN KEY sont ajoutées, toutes les données existantes sont vérifiées afin de détecter d'éventuelles violations de contraintes, à moins que l'option WITH NOCHECK ne soit spécifiée. Si tel est le cas, l'instruction ALTER TABLE échoue et une erreur est renvoyée. Lorsqu'une nouvelle contrainte PRIMARY KEY ou UNIQUE est ajoutée à une colonne existante, les données de la ou des colonnes doivent être uniques. L'instruction ALTER TABLE échoue si des valeurs sont en double. L'option WITH NOCHECK n'a aucun effet lorsque vous ajoutez une contrainte PRIMARY KEY ou UNIQUE.  
  
 Chaque contrainte PRIMARY KEY et UNIQUE génère un index. Quel que soit le nombre de contraintes UNIQUE et PRIMARY KEY, le nombre d'index sur la table ne peut en aucun cas dépasser 999 index cluster et 1 index cluster. Les contraintes FOREIGN KEY ne génèrent pas automatiquement un index. Toutefois, les colonnes clés étrangères sont souvent employées dans les critères de jointure dans des requêtes grâce à la correspondance de la ou des colonnes de la contrainte de clé étrangère d'une table avec la ou les colonne(s) clé(s) unique(s) ou primaire(s) de l'autre table. Un index sur les colonnes clés étrangères permet au [!INCLUDE[ssDE](../../includes/ssde-md.md)] de rechercher rapidement des données associées dans la table de clés étrangères.  
  
## <a name="examples"></a>Exemples  
 Pour obtenir des exemples, consultez [ALTER TABLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-table-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [column_definition &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-column-definition-transact-sql.md)  
  
  

