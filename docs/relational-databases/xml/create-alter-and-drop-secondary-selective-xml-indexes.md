---
title: "Cr&#233;er, modifier ou supprimer des index XML secondaires s&#233;lectifs | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
caps.latest.revision: 8
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 7
---
# Cr&#233;er, modifier ou supprimer des index XML secondaires s&#233;lectifs
  Décrit la procédure de création d'un index XML secondaire sélectif, ou de modification ou de suppression d'un index XML secondaire sélectif existant.  
  
##  <a name="create"></a> Création d'un index XML secondaire sélectif  
  
### Procédure : créer un index XML secondaire sélectif  
 **Créer un index XML secondaire sélectif à l'aide de Transact-SQL**  
 Créez un index XML secondaire sélectif en appelant l'instruction CREATE XML INDEX. Pour plus d’informations, consultez [CREATE XML INDEX &#40;Selective XML Indexes&#41;](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
 **Exemple**  
  
 L'exemple suivant crée un index XML secondaire sélectif sur le chemin d'accès `'pathabc'`. Le chemin d'accès à l'index est identifié par le nom qui lui a été donné lors de sa création à l'aide de l'instruction CREATE SELECTIVE XML INDEX. Pour plus d’informations, consultez [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
```tsql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
 [Dans cette rubrique](#top)  
  
##  <a name="alter"></a> Modification d'un index XML secondaire sélectif  
 L'instruction ALTER n'est pas prise en charge pour les index XML secondaires sélectifs. Pour modifier un index XML secondaire sélectif, supprimez l'index existant et recréez-le.  
  
### Procédure : modifier un index XML secondaire sélectif  
 **Modifier un index XML secondaire sélectif à l'aide de Transact-SQL**  
 1.  Supprimez l'index XML secondaire sélectif existant en appelant l'instruction DROP INDEX. Pour plus d’informations, consultez [DROP INDEX &#40;Selective XML Indexes&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
2.  Recréez l'index avec les options de votre choix en appelant l'instruction CREATE XML INDEX. Pour plus d’informations, consultez [CREATE XML INDEX &#40;Selective XML Indexes&#41;](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
 **Exemple**  
  
 L'exemple suivant modifie un index XML secondaire sélectif en le supprimant et en le recréant.  
  
```tsql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
 [Dans cette rubrique](#top)  
  
##  <a name="drop"></a> Suppression d'un index XML secondaire sélectif  
  
### Procédure : supprimer un index XML secondaire sélectif  
 **Supprimer un index XML secondaire sélectif à l'aide de Transact-SQL**  
 Supprimez un index XML secondaire sélectif en appelant l'instruction DROP INDEX. Pour plus d’informations, consultez [DROP INDEX &#40;Selective XML Indexes&#41;](../../t-sql/statements/drop-index-selective-xml-indexes.md).  
  
 **Exemple**  
  
 L'exemple suivant illustre une instruction DROP INDEX.  
  
```tsql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
 [Dans cette rubrique](#top)  
  
## Voir aussi  
 [Index XML sélectifs &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  