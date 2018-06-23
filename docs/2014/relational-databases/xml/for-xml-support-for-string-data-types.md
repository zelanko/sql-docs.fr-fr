---
title: Prise en charge de FOR XML pour les types de données string | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strings [SQL Server], XML
ms.assetid: bf069da8-de1e-44d2-a1fb-ade383076ac1
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f44b0158e539d91cba8bfe03587eaf63800c9d9d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142626"
---
# <a name="for-xml-support-for-string-data-types"></a>Prise en charge de FOR XML pour les types de données string
  Le code XML généré par les espaces blancs FOR XML dans les données est décomposé en entités.  
  
 Dans l’exemple ci-dessous, un exemple de table **T** est créé et des données y sont insérées parmi lesquelles les caractères saut de ligne, retour chariot et tabulation. L'instruction SELECT extrait les données de la table.  
  
```  
CREATE TABLE T  
(  
  c1 int identity primary key,  
  c2 varchar(100)  
);  
go  
  
INSERT T (c2) VALUES ('Special character 0xD for carriage return ' + convert(varchar(10), 0xD) + ' after carriage return');  
INSERT T (c2) VALUES ('Special character 0x9 for tab ' + convert(varchar(10), 0x9) + ' after tab' );  
INSERT T (c2) VALUES ('Special character 0xA for line feed ' + convert(varchar(10), 0xA) + ' after line feed');  
go  
SELECT *   
FROM T  
FOR XML AUTO;  
go  
```  
  
 Voici le résultat obtenu :  
  
```  
 <T c1="1" c2="Special character 0xD for carriage return   
 after carriage return" />  
 <T c1="2" c2="Special character 0x9 for tab     after tab" />  
 <T c1="3" c2="Special character 0xA for line feed   
after line feed" />  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le retour chariot de la première ligne est défini comme l'entité &#xD.  
  
-   La tabulation de la deuxième ligne est définie comme l'entité &#x09.  
  
-   Le saut de ligne de la troisième ligne est défini comme l'entité &#xA.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge FOR XML des différents types de données SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  