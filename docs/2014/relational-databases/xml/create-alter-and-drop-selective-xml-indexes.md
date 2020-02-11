---
title: Créer, modifier ou supprimer des index XML sélectifs | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: c398f396-f630-4a2d-a264-f243c5346de1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a95fa1c010197d0107c757198d9db7eaf8d3c42e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62637597"
---
# <a name="create-alter-and-drop-selective-xml-indexes"></a>Créer, modifier ou supprimer des index XML sélectifs
  Décrit la procédure de création d'un index XML sélectif, ou de modification ou de suppression d'un index XML sélectif existant.  
  
 Pour plus d’informations sur les index XML sélectifs, consultez [Index XML sélectifs &#40;SXI&#41;](selective-xml-indexes-sxi.md).  
  
##  <a name="create"></a> Création d'un index XML sélectif  
  
### <a name="how-to-create-a-selective-xml-index"></a>Procédure : créer un index XML sélectif  
 **Créer un index XML sélectif à l'aide de Transact-SQL**  
 Créez un index XML sélectif en appelant l'instruction CREATE SELECTIVE XML INDEX. Pour plus d’informations, consultez [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql).  
  
 **Exemple**  
  
 L'exemple suivant montre la syntaxe pour créer un index XML sélectif. Il montre également différentes variantes de la syntaxe pour décrire les chemins d'accès à indexer, avec des indicateurs facultatifs d'optimisation.  
  
```sql  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()'  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
)  
```  
  
  
  
##  <a name="alter"></a> Modification d'un index XML sélectif  
  
### <a name="how-to-alter-a-selective-xml-index"></a>Procédure : modifier un index XML sélectif  
 **Modifier un index XML sélectif à l'aide de Transact-SQL**  
 Modifiez un index XML sélectif existant en appelant l'instruction ALTER INDEX. Pour plus d’informations, consultez [ALTER INDEX &#40;index XML sélectifs&#41;](../indexes/indexes.md).  
  
 **Exemple**  
  
 L'exemple suivant illustre une instruction ALTER INDEX. Cette instruction ajoute le chemin `'/a/b/m'` à la partie XQuery de l’index et supprime le chemin `'/a/b/e'` de la partie SQL de l’index créé dans l’exemple de la rubrique [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-selective-xml-index-transact-sql). Le chemin d'accès à supprimer est identifié par le nom qui lui a été donné lors de sa création.  
  
```sql  
ALTER INDEX sxi_index  
ON Tbl  
FOR   
(  
    ADD pathm = '/a/b/m' as XQUERY 'node()' ,  
    REMOVE pathabe  
)  
```  
  
  
  
##  <a name="drop"></a> Suppression d'un index XML sélectif  
  
### <a name="how-to-drop-a-selective-xml-index"></a>Procédure : supprimer un index XML sélectif  
 **Supprimer un index XML sélectif à l'aide de Transact-SQL**  
 Supprimez un index XML sélectif en appelant l'instruction DROP INDEX. Pour plus d’informations, consultez [DROP INDEX &#40;index XML sélectifs&#41;](/sql/t-sql/statements/drop-index-selective-xml-indexes).  
  
 **Exemple**  
  
 L'exemple suivant illustre une instruction DROP INDEX.  
  
```sql  
DROP INDEX sxi_index ON tbl  
```  
  
 
  
  
