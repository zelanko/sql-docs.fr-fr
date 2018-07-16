---
title: Type de données (API de procédure stockée étendue) | Microsoft Docs
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
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
caps.latest.revision: 29
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6bbf8c994f86502dd43b26ef588d864aa4dbbc4a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37208989"
---
# <a name="data-types-extended-stored-procedure-api"></a>Type de données (API de procédure stockée étendue)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Pour utiliser les types de données de l'API de procédure stockée étendue, incluez le fichier d'en-tête Srv.h dans votre programme.  
  
|Type de données|Type de données SQL Server|Description|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|`binary`|Type de données `binary`, de longueur comprise entre 0 et 8 000 octets.|  
|SRVBIGCHAR|`char`|Type de données `character`, de longueur comprise entre 0 et 8 000 octets.|  
|SRVBIGVARBINARY|`varbinary`|Type de données `binary` de longueur variable comprise entre 0 et 8 000 octets.|  
|SRVBIGVARCHAR|`varchar`|Type de données `character` de longueur variable comprise entre 0 et 8 000 octets.|  
|SRVBINARY|`binary`|`binary` type de données.|  
|SRVBIT|`Bit`|`bit` type de données.|  
|SRVBITN|`bit null`|Type de données `bit` autorisant les valeurs NULL.|  
|SRVCHAR|`char`|`character` type de données.|  
|SRVDATETIME|`datetime`|Type de données `datetime` de 8 octets.|  
|SRVDATETIM4|`smalldatetime`|4 octets `smalldatetime` type de données.|  
|SRVDATETIMN|**datetime null**|Type de données `smalldatetime` ou `datetime` autorisant les valeurs NULL.|  
|SRVDECIMAL|`decimal`|`decimal` type de données.|  
|SRVDECIMALN|`decimal null`|Type de données `decimal` autorisant les valeurs NULL.|  
|SRVFLT4|`real`|4 octets `real` type de données.|  
|SRVFLT8|`float`|Type de données `float` de 8 octets.|  
|SRVFLTN|`real` &#124; `float null`|Type de données `real` ou `float` autorisant les valeurs NULL.|  
|SRVIMAGE|`image`|`image` type de données.|  
|SRVINT1|`tinyint`|1 octet `tinyint` type de données.|  
|SRVINT2|`smallint`|2 octets `smallint` type de données.|  
|SRVINT4|`int`|4 octets `int` type de données.|  
|SRVINTN|`tinyint` &#124; `smallint` &#124; `int null`|Type de données `tinyint`, `smallint` ou `int` autorisant les valeurs NULL.|  
|SRVMONEY4|`smallmoney`|4 octets `smallmoney` type de données.|  
|SRVMONEY|`money`|Type de données `money` de 8 octets.|  
|SRVMONEYN|`money` &#124; `smallmoney null`|Type de données `smallmoney` ou `money` autorisant les valeurs NULL.|  
|SRVNCHAR|**nchar**|Type de données `character` Unicode.|  
|SRVNTEXT|`ntext`|Type de données `text` Unicode.|  
|SRVNUMERIC|`numeric`|`numeric` type de données.|  
|SRVNUMERICN|`numeric null`|Type de données `numeric` autorisant les valeurs NULL.|  
|SRVNVARCHAR|**nvarchar**|Type de données `character` de longueur variable Unicode.|  
|SRVTEXT|`text`|`text` type de données.|  
|SRVVARBINARY|`varbinary`|Type de données `binary` de longueur variable.|  
|SRVVARCHAR|`varchar`|Type de données `character` de longueur variable.|  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
