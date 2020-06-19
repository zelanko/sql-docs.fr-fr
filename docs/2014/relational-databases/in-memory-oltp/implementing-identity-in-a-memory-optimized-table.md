---
title: Implémentation d’IDENTITY dans une table optimisée en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c0a704a3-3a31-4c2c-b967-addacda62ef8
author: rothja
ms.author: jroth
ms.openlocfilehash: 793890018d0d7e57e4102d03a9120feb9803b816
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050130"
---
# <a name="implementing-identity-in-a-memory-optimized-table"></a>Implémentation d'IDENTITY dans une table optimisée en mémoire
  IDENTITY(1, 1) est pris en charge sur une table mémoire optimisée. Cependant, les colonnes d'identité avec définition IDENTITY(x, y) où x != 1 ou y != 1 ne sont pas prises en charge sur les tables mémoire optimisées. La solution pour les valeurs IDENTITY utilise l'objet SEQUENCE ([Sequence Numbers](../sequence-numbers/sequence-numbers.md)).  
  
 Supprimez d'abord la propriété IDENTITY de la table que vous convertissez en OLTP en mémoire. Ensuite, définissez un nouvel objet SEQUENCE pour la colonne de la table. Les objets SEQUENCE en tant que colonnes d'identité s'appuient sur la possibilité de créer des valeurs PAR DÉFAUT pour les colonnes qui utilisent la syntaxe NEXT VALUE FOR pour obtenir une nouvelle valeur d'identité. Étant donné que les valeurs par défaut ne sont pas prises en charge dans OLTP en mémoire, vous devez passer la valeur SEQUENCE récemment générée à l'instruction INSERT ou à une procédure stockée compilée en mode natif qui exécute l'insertion. L'exemple ci-dessous illustre ce modèle.  
  
```sql  
-- Create a new In-Memory OLTP table to simulate IDENTITY insert  
-- Here the column C1 was the identity column in the original table  
--  
create table T1  
(  
  
[c1] integer not null primary key T1_c1 nonclustered,  
[c2] varchar(32) not null,  
[c3] datetime not null  
  
) with (memory_optimized = on)  
go  
  
-- This is a sequence provider that will give us values for column [c1]  
--  
create sequence usq_SequenceForT1 as integer start with 2 increment by 1  
go  
  
--   insert a sample row using the sequence  
--   note that a new value needs to be retrieved form   
--   the sequence object for every insert  
--  
declare @c1 integer = next value for [dbo].[usq_SequenceForT1]  
insert into T1 values (@c1, 'test', getdate())  
```  
  
 Après avoir effectué l'insertion plusieurs fois, vous voyez les valeurs à croissance monotone valides dans la colonne [c1]. Ce jeu de résultats est généré à l'aide de l'analyse de table et de l'index de hachage sans `ORDER BY` ; par conséquent, les lignes ne sont pas ordonnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Migration vers l’OLTP en mémoire](migrating-to-in-memory-oltp.md)  
  
  
