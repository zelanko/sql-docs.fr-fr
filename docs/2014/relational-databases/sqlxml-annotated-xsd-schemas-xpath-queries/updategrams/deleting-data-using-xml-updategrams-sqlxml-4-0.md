---
title: Suppression des données à l’aide de codes XML (SQLXML 4.0) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32134713be17a0770eb58d69529cc34691c181a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053251"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>Suppression de données à l'aide de codes de mise à jour (updategrams) XML (SQLXML 4.0)
  Une mise à jour indique une opération de suppression lorsqu’une instance d’enregistrement apparaît dans les  **\<avant >** bloc sans enregistrements correspondants dans le  **\<après >** bloc. Dans ce cas, la mise à jour supprime l’enregistrement dans le  **\<avant >** bloc à partir de la base de données.  
  
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
  
 Vous pouvez omettre le  **\<après >** balise si la mise à jour effectue uniquement une opération de suppression. Si vous ne spécifiez pas le paramètre facultatif `mapping-schema` attribut, le  **\<ElementName >** spécifiés dans les mappages de mise à jour à une table de base de données et l’enfant éléments ou attributs sont mappés aux colonnes dans la table.  
  
 Si un élément spécifié dans la mise à jour correspond à plusieurs lignes dans la table ou ne correspond pas à n’importe quelle ligne, la mise à jour renvoie une erreur et annule l’intégralité  **\<synchronisation >** bloc. Un seul enregistrement peut être supprimé à la fois par un élément dans le code de mise à jour.  
  
## <a name="examples"></a>Exemples  
 Les exemples dans cette section utilisent le mappage par défaut (en d'autres termes, aucun schéma de mappage n'est spécifié dans le code de mise à jour). Pour plus d’exemples de codes qui utilisent des schémas de mappage, consultez [spécification d’un schéma de mappage annoté dans une mise à jour &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
 Pour créer des exemples fonctionnels à l’aide de la procédure ci-après, vous devez respecter la configuration requise spécifiée dans [configuration requise pour exécuter les exemples de SQLXML](../../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>A. Suppression d'un enregistrement à l'aide d'un code de mise à jour  
 Les codes de mise à jour suivants suppriment deux enregistrements de la table HumanResources.Shift.  
  
 Dans ces exemples, le code de mise à jour ne spécifie pas de schéma de mappage. Par conséquent, le code de mise à jour utilise le mappage par défaut, dans lequel le nom d'élément est mappé à un nom de table et les attributs ou sous-éléments sont mappés aux colonnes.  
  
 Cette mise à jour première est centré sur les attributs et identifie deux décalages (Day-Evening et Evening-Night) dans le  **\<avant >** bloc. Étant donné qu’aucun enregistrement correspondant dans le  **\<après >** bloc, il s’agit d’une opération de suppression.  
  
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
  
1.  Effectuez l’exemple B (« insertion de plusieurs enregistrements à l’aide d’une mise à jour ») dans [insertion de données à l’aide de programmes &#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
2.  Copiez la mise à jour ci-dessus dans le bloc-notes et enregistrez-le en tant que Updategram-Removeshifts dans le même dossier que celui utilisé pour terminer (« insertion de plusieurs enregistrements à l’aide d’une mise à jour ») dans [insertion de données à l’aide de programmes &#40;SQLXML 4.0&#41; ](inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le code de mise à jour (updategram).  
  
     Pour plus d’informations, consultez [à l’aide d’ADO pour exécuter des requêtes SQLXML 4.0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations de sécurité de mise à jour &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  