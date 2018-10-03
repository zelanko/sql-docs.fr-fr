---
title: Prise en charge de FOR XML pour les types de données string | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- strings [SQL Server], XML
ms.assetid: bf069da8-de1e-44d2-a1fb-ade383076ac1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 48a6063193b0ad629316bb1a7d6180c27178561b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076679"
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
  
  
