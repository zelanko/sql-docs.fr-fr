---
title: Type de données (API de procédure stockée étendue) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e135e6706454fe1f03b4c7ab762e5234e1b7d35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064214"
---
# <a name="data-types-extended-stored-procedure-api"></a>Type de données (API de procédure stockée étendue)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 Pour utiliser les types de données de l'API de procédure stockée étendue, incluez le fichier d'en-tête Srv.h dans votre programme.  
  
|Type de données|Type de données SQL Server|Description|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|**binary**|type de données **Binary** , longueur comprise entre 0 et 8000 octets.|  
|SRVBIGCHAR|**char**|type de données **character** , longueur comprise entre 0 et 8000 octets.|  
|SRVBIGVARBINARY|**varbinary**|Type de données **binary** de longueur variable comprise entre 0 et 8000 octets.|  
|SRVBIGVARCHAR|**varchar**|Type de données **character** de longueur variable comprise entre 0 et 8000 octets.|  
|SRVBINARY|**binary**|type de données **Binary** .|  
|SRVBIT|**64bits**|type de données **bit** .|  
|SRVBITN|**bit null**|type de données **bit** , valeurs NULL autorisées.|  
|SRVCHAR|**char**|type de données **character** .|  
|SRVDATETIME|**DATETIME**|Type de données **datetime** sur 8 octets|  
|SRVDATETIM4|**smalldatetime**|Type de données **smalldatetime** sur 4 octets|  
|SRVDATETIMN|**DateTime null**|type de données **smalldatetime** ou **DateTime** , valeurs NULL autorisées.|  
|SRVDECIMAL|**sépar**|type de données **Decimal** .|  
|SRVDECIMALN|**décimal null**|type de données **Decimal** , valeurs NULL autorisées.|  
|SRVFLT4|**real**|Type de données **real** sur 4 octets|  
|SRVFLT8|**float**|Type de données **float** sur 8 octets|  
|SRVFLTN|**réel** &#124; **float null**|type de données **Real** ou **float** , valeurs NULL autorisées.|  
|SRVIMAGE|**image**|type de données **image** .|  
|SRVINT1|**tinyint**|Type de données **tinyint** sur 1 octet.|  
|SRVINT2|**smallint**|Type de données **smallint** sur 2 octets.|  
|SRVINT4|**int**|Type de données **int** sur 4 octets|  
|SRVINTN|**tinyint** &#124; **smallint** &#124; **int null**|type de données **tinyint**, **smallint**ou **int** , valeurs NULL autorisées.|  
|SRVMONEY4|**SMALLMONEY**|Type de données **smallmoney** sur 4 octets|  
|SRVMONEY|**money**|Type de données **money** sur 8 octets|  
|SRVMONEYN|**money** &#124; **smallmoney null**|type de données **smallmoney** ou **Money** , valeurs NULL autorisées.|  
|SRVNCHAR|**nchar**|Type de données **character** Unicode.|  
|SRVNTEXT|**ntext**|Type de données **text** Unicode.|  
|SRVNUMERIC|**chiffre**|type de données **numérique** .|  
|SRVNUMERICN|**valeur numérique null**|type de données **Numeric** , valeurs NULL autorisées.|  
|SRVNVARCHAR|**nvarchar**|Type de données **character** de longueur variable Unicode.|  
|SRVTEXT|**text**|type de données **Text** .|  
|SRVVARBINARY|**varbinary**|Type de données **binary** de longueur variable.|  
|SRVVARCHAR|**varchar**|Type de données **character** de longueur variable.|  
  
> [!IMPORTANT]  
>  Il est préférable d'examiner avec soin le code source des procédures stockées étendues et de tester les DLL compilées avant de les installer sur un serveur de production. Pour plus d'informations sur l'examen et les tests de sécurité, consultez ce [site Web de Microsoft](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
