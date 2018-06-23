---
title: Gérer les index de recherche en texte intégral | Documents Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 28ff17dc-172b-4ac4-853f-990b5dc02fd1
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9a38476f427cbc2c9630c66020f35c5f7355e9bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142329"
---
# <a name="manage-full-text-indexes"></a>Gérer les index de recherche en texte intégral
     
##  <a name="view"></a> Affichage et modification des propriétés d’un Index de recherche en texte intégral  
  
#### <a name="to-view-or-change-the-properties-of-a-full-text-index-in-management-studio"></a>Pour afficher ou modifier les propriétés d'un index de recherche en texte intégral dans Management Studio  
  
1.  Dans l'Explorateur d'objets, développez le serveur.  
  
2.  Développez **Bases de données**, puis la base de données qui contient l’index de recherche en texte intégral.  
  
3.  Développez **Tables**.  
  
4.  Cliquez avec le bouton droit sur la table sur laquelle l’index de recherche en texte intégral est défini, sélectionnez **Index de recherche en texte intégral**et, dans le menu contextuel **Index de recherche en texte intégral** , cliquez sur **Propriétés**. La boîte de dialogue **Propriétés d’index de recherche en texte intégral** s’affiche.  
  
5.  Dans le volet **Sélectionner une page** , vous pouvez sélectionner l’une des pages suivantes :  
  
    |Radiomessagerie|Description|  
    |----------|-----------------|  
    |**Général**|Affiche les propriétés de base de l'index de recherche en texte intégral. Il s'agit de plusieurs propriétés modifiables et non modifiables telles que le nom de la base de données, le nom de la table et le nom de la colonne clé de recherche en texte intégral. Les propriétés modifiables sont les suivantes :<br /><br /> **Liste de mots vides de l’index de recherche en texte intégral**<br /><br /> **Indexation de texte intégral activée**<br /><br /> **Suivi des modifications**<br /><br /> **Liste de propriétés de recherche**<br /><br /> <br /><br /> Pour plus d’informations, consultez [propriétés d’Index de recherche en texte intégral &#40;Général Page&#41;](full-text-index-properties-general-page.md).|  
    |**Colonnes**|Affiche les colonnes de table qui sont disponibles pour l'indexation de texte intégral. La ou les colonnes sélectionnées sont indexées en texte intégral. Vous pouvez sélectionner autant de colonnes disponibles que vous souhaitez inclure dans l'index de recherche en texte intégral. Pour plus d’informations, consultez [propriétés d’Index de recherche en texte intégral &#40;Page colonnes&#41;](../../2014/database-engine/full-text-index-properties-columns-page.md).|  
    |**Planifications**|Utilisez cette page afin de créer ou gérer des planifications pour un travail de l'Agent SQL Server qui démarre un remplissage incrémentiel de la table pour remplir l'index de recherche en texte intégral. Pour plus d’informations, consultez [Alimenter des index de recherche en texte intégral](../relational-databases/indexes/indexes.md).<br /><br /> **\*\* Important \* \***  après avoir quitté le **propriétés d’Index de recherche en texte intégral** boîte de dialogue, n’importe quelle planification nouvellement créée est associée à un travail de l’Agent SQL Server (Démarrer alimentation de Table incrémentielle sur *nom_base_de_données*. *nom_table*).|  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)] pour enregistrer vos modifications et fermer la boîte de dialogue **Propriétés d’index de recherche en texte intégral**.  
  
##  <a name="props"></a> Affichage des propriétés des colonnes et Tables indexées  
 Vous pouvez faire appel à plusieurs fonctions [!INCLUDE[tsql](../includes/tsql-md.md)], comme OBJECTPROPERTYEX, pour vous procurer la valeur de diverses propriétés d'indexation de texte intégral. Ces informations sont utiles pour administrer la recherche en texte intégral et résoudre les problèmes qui la concernent.  
  
 Le tableau ci-après recense les propriétés en texte intégral liées aux colonnes et tables indexées, ainsi que les fonctions [!INCLUDE[tsql](../includes/tsql-md.md)] qui leur sont associées.  
  
|Propriété|Description|Fonction|  
|--------------|-----------------|--------------|  
|`FullTextTypeColumn`|TYPE COLUMN de la table qui contient les informations sur le type de document de la colonne.|[COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql)|  
|`IsFulltextIndexed`|Indique si une colonne a été activée pour l'indexation de texte intégral.|COLUMNPROPERTY|  
|`IsFulltextKey`|Indique si l'index représente la clé de texte intégral d'une table.|[INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql)|  
|**TableFulltextBackgroundUpdateIndexOn**|Indique si une table possède une indexation de mise à jour d'arrière-plan de texte intégral.|[OBJECTPROPERTYEX](/sql/t-sql/functions/objectproperty-transact-sql)|  
|`TableFulltextCatalogId`|ID du catalogue de texte intégral dans lequel résident les données d'indexation de texte intégral de la table.|OBJECTPROPERTYEX|  
|`TableFulltextChangeTrackingOn`|Indique si le suivi des modifications de texte intégral est activé pour la table.|OBJECTPROPERTYEX|  
|`TableFulltextDocsProcessed`|Nombre de lignes traitées depuis le démarrage de l'indexation de texte intégral.|OBJECTPROPERTYEX|  
|**TableFulltextFailCount**|Nombre de lignes que la recherche en texte intégral n'a pas indexées.|OBJECTPROPERTYEX|  
|**TableFulltextItemCount**|Nombre de lignes dont l'indexation de texte intégral a réussi.|OBJECTPROPERTYEX|  
|`TableFulltextKeyColumn`|ID de la colonne clé unique de texte intégral.|OBJECTPROPERTYEX|  
|`TableFullTextMergeStatus`|Indique s'il s'agit d'une table qui a un index de recherche en texte intégral qui est en cours de fusion.|OBJECTPROPERTYEX|  
|**TableFulltextPendingChanges**|Nombre d'entrées de suivi des modifications en attente de traitement.|OBJECTPROPERTYEX|  
|`TableFulltextPopulateStatus`|État de remplissage de la table de texte intégral.|OBJECTPROPERTYEX|  
|`TableHasActiveFulltextIndex`|Indique si une table possède un index de recherche en texte intégral actif.|OBJECTPROPERTYEX|  
  
##  <a name="key"></a> Obtention d’informations sur la colonne de clé de recherche en texte intégral  
 En général, le résultat des fonctions d'ensemble de lignes CONTAINSTABLE ou FREETEXTTABLE doit être joint avec la table de base. Dans ce cas-là, vous devez connaître le nom de la colonne clé unique. Vous pouvez déterminer si un index unique donné est utilisé comme clé de texte intégral et obtenir l'identificateur de la colonne clés de texte intégral.  
  
#### <a name="to-inquire-whether-a-given-unique-index-is-used-as-the-full-text-key-column"></a>Pour déterminer si un index unique donné est utilisé comme colonne clés de texte intégral  
  
1.  Utilisez une instruction [SELECT](/sql/t-sql/queries/select-transact-sql) pour appeler la fonction [INDEXPROPERTY](/sql/t-sql/functions/indexproperty-transact-sql). Dans la fonction appel utilisez la fonction OBJECT_ID pour convertir le nom de la table (*table_name*) en ID de table, spécifiez le nom d’un index unique pour la table et indiquez le `IsFulltextKey` index, propriété, comme suit :  
  
    ```  
    SELECT INDEXPROPERTY( OBJECT_ID('table_name'), 'index_name',  'IsFulltextKey' );  
    ```  
  
     L'instruction retourne la valeur 1 si l'index est utilisé pour garantir l'unicité de la colonne clé de texte intégral, et la valeur 0 dans le cas contraire.  
  
 **Exemple**  
  
 L'exemple suivant permet de déterminer si l'index `PK_Document_DocumentID` est utilisé pour garantir l'unicité de la colonne clé de texte intégral, comme suit :  
  
```  
USE AdventureWorks  
GO  
SELECT INDEXPROPERTY ( OBJECT_ID('Production.Document'), 'PK_Document_DocumentID',  'IsFulltextKey' )  
```  
  
 Cet exemple retourne la valeur 1 si l'index `PK_Document_DocumentID` est utilisé pour garantir l'unicité de la colonne clés de texte intégral. Si tel n'est pas le cas, la valeur 0 ou une valeur Null est retournée. La valeur Null signifie que vous utilisez un nom d'index non valide, que le nom d'index ne correspond pas à la table, que la table n'existe pas, etc.  
  
#### <a name="to-find-the-identifier-of-the-full-text-key-column"></a>Pour rechercher l'identificateur de la colonne clé de texte intégral  
  
1.  Chaque table activée pour la recherche en texte intégral comporte une colonne qui est utilisée pour garantir l’unicité des lignes de la table (*colonne de clés**unique*). La propriété `TableFulltextKeyColumn`, obtenue à l'aide de la fonction OBJECTPROPERTYEX, contient l'ID de colonne de la colonne clé unique.  
  
     Pour obtenir cet identificateur, vous pouvez utiliser une instruction SELECT afin d'appeler la fonction OBJECTPROPERTYEX. Utilisez la fonction OBJECT_ID pour convertir le nom de la table (*table_name*) en ID de table et spécifiez le `TableFulltextKeyColumn` propriété, comme suit :  
  
    ```  
    SELECT OBJECTPROPERTYEX(OBJECT_ID( 'table_name'), 'TableFulltextKeyColumn' ) AS 'Column Identifier';  
    ```  
  
 **Exemples**  
  
 L'exemple ci-après retourne l'identificateur de la colonne clé de texte intégral ou une valeur Null. La valeur Null signifie que vous utilisez un nom d'index non valide, que le nom d'index ne correspond pas à la table, que la table n'existe pas, etc.  
  
```  
USE AdventureWorks;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('Production.Document'), 'TableFulltextKeyColumn');  
GO  
```  
  
 L'exemple ci-après explique comment utiliser l'identificateur de la colonne clé unique pour obtenir le nom de la colonne.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @key_column sysname  
SET @key_column = Col_Name(Object_Id('Production.Document'),  
ObjectProperty(Object_id('Production.Document'),  
'TableFulltextKeyColumn')   
)  
SELECT @key_column AS 'Unique Key Column';  
GO  
```  
  
 Cet exemple retourne une colonne de jeu de résultats appelée `Unique Key Column`, qui contient une seule ligne indiquant le nom de la colonne clé unique de la table Document, DocumentID. Notez que, si cette requête contenait un nom d'index non valide, si le nom d'index ne correspondait pas à la table, si la table n'existait pas, etc., une valeur NULL serait retournée.  
  
##  <a name="disable"></a> La désactivation ou réactivation d’une Table pour l’indexation de texte intégral  
 Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], par défaut, toutes les bases de données créées par les utilisateurs sont activées pour la recherche en texte intégral. De plus, une table individuelle est automatiquement activée pour l'indexation de texte intégral dès qu'un index de recherche en texte intégral est créé sur cette table et qu'une colonne est ajoutée à l'index. Une table est automatiquement désactivée pour l'indexation de recherche en texte intégral lorsque la dernière colonne est supprimée de son index de texte intégral.  
  
 Dans une table à index de recherche en texte intégral, vous pouvez désactiver ou réactiver manuellement une table pour l'indexation de recherche en texte intégral en utilisant [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-enable-a-table-for-full-text-indexing"></a>Pour activer une table pour l'indexation de recherche en texte intégral  
  
1.  Développez le groupe de serveurs, **Bases de données**, puis la base de données qui contient la table à activer pour l’indexation de texte intégral.  
  
2.  Développez **Tables**et cliquez avec le bouton droit sur la table que vous souhaitez désactiver ou réactiver pour l’indexation de texte intégral.  
  
3.  Sélectionnez **Index de recherche en texte intégral**, puis cliquez sur **Disable Full-Text index** (Désactiver l’index de recherche en texte intégral) ou **Enable Full-Text index**(Activer l’index de recherche en texte intégral).  
  
##  <a name="remove"></a> Suppression d’un Index de recherche en texte intégral d’une Table  
  
#### <a name="to-remove-a-full-text-index-from-a-table"></a>Pour supprimer un index de recherche en texte intégral d'une table  
  
1.  Dans l'Explorateur d'objets, cliquez avec le bouton droit sur la table dotée de l'index de recherche en texte intégral à supprimer.  
  
2.  Sélectionnez **Supprimer l’index de recherche en texte intégral**.  
  
3.  Quand le système vous y invite, cliquez sur **OK** pour confirmer la suppression de l’index de recherche en texte intégral.  
  
  
