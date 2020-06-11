---
title: Suppression de données à l’aide de codes XML (SQLXML)
description: En savoir plus sur la suppression de données à l’aide d’un mise à jour XML dans SQLXML 4,0.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f32c1107d886b7bc84590abbd6bab5343d2a2b8b
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529820"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>Suppression de données à l'aide de codes de mise à jour (updategrams) XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Un mise à jour indique une opération de suppression lorsqu’une instance d’enregistrement apparaît dans le **\<before>** bloc sans enregistrements correspondants dans le **\<after>** bloc. Dans ce cas, le mise à jour supprime l’enregistrement du bloc de **\<before>** la base de données.  
  
 Voici le format du code de mise à jour pour une opération de suppression :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 Vous pouvez omettre la **\<after>** balise si le mise à jour exécute uniquement une opération de suppression. Si vous ne spécifiez pas l’attribut **mapping-schema** facultatif, le **\<ElementName>** spécifié dans le mise à jour est mappé à une table de base de données et les éléments ou attributs enfants sont mappés aux colonnes de la table.  
  
 Si un élément spécifié dans le mise à jour correspond à plusieurs lignes de la table ou qu’il ne correspond à aucune ligne, mise à jour retourne une erreur et annule l’intégralité du **\<sync>** bloc. Un seul enregistrement peut être supprimé à la fois par un élément dans le code de mise à jour.  
  
## <a name="examples"></a>Exemples  
 Les exemples dans cette section utilisent le mappage par défaut (en d'autres termes, aucun schéma de mappage n'est spécifié dans le code de mise à jour). Pour obtenir plus d’exemples de codes qui utilisent des schémas de mappage, consultez [spécification d’un schéma de mappage annoté dans un mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
 Pour créer des exemples fonctionnels à l’aide des exemples suivants, vous devez respecter les exigences spécifiées dans la [Configuration requise pour l’exécution d’exemples SQLXML](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>R. Suppression d'un enregistrement à l'aide d'un code de mise à jour  
 Les codes de mise à jour suivants suppriment deux enregistrements de la table HumanResources.Shift.  
  
 Dans ces exemples, le code de mise à jour ne spécifie pas de schéma de mappage. Par conséquent, le code de mise à jour utilise le mappage par défaut, dans lequel le nom d'élément est mappé à un nom de table et les attributs ou sous-éléments sont mappés aux colonnes.  
  
 Ce premier mise à jour est centré sur les attributs et identifie deux décalages (jour-soirée et soir-nuit) dans le **\<before>** bloc. Étant donné qu’il n’y a aucun enregistrement correspondant dans le **\<after>** bloc, il s’agit d’une opération de suppression.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Complétez l’exemple B (« insertion de plusieurs enregistrements à l’aide d’un mise à jour ») lors de l' [insertion de données à l’aide de XML codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
2.  Copiez le mise à jour ci-dessus dans le bloc-notes et enregistrez-le en tant que Updategram-RemoveShifts.xml dans le même dossier que celui utilisé pour la finalisation (« insertion de plusieurs enregistrements à l’aide d’un mise à jour ») lors de l' [insertion de données à l’aide de XML codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le code de mise à jour (updategram).  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
