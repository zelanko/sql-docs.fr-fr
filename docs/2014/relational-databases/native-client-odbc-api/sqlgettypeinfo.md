---
title: SQLGetTypeInfo | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60c4c4d364f9c07e9ca241dd357535f7f7acb42d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046685"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les rapports de pilote ODBC Native Client définie de la colonne USERTYPE supplémentaire dans le résultat de `SQLGetTypeInfo`. USERTYPE signale la définition de type de données de bibliothèque de bases de données et est utile aux développeurs qui déplacent des applications de bibliothèque de bases de données existantes vers ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite l'identité comme un attribut, tandis que ODBC la traite comme un type de données. Pour résoudre cette incohérence, `SQLGetTypeInfo` retourne les types de données : **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity** , et **numericidentity**. Le `SQLGetTypeInfo` colonne du jeu de résultats AUTO_UNIQUE_VALUE signale la valeur TRUE pour ces types de données.  
  
 Pour **varchar**, **nvarchar** et **varbinary**, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client continue de signaler les 8000, 4000 et 8000 respectivement pour COLUMN_SIZE valeur, même s’il est en réalité illimitée. Ceci a pour but de garantir la compatibilité descendante.  
  
 Pour le **xml** type de données, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client indique SQL_SS_LENGTH_UNLIMITED pour COLUMN_SIZE afin de dénoter une taille illimitée.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo et paramètres table  
 Le type de table pour les paramètres table est effectivement un meta-type-, un type utilisé pour définir d’autres types. Par conséquent, il ne devra pas être exposés via SQLGetTypeInfo. Applications doivent utiliser SQLTables, plutôt que de SQLGetTypeInfo, pour récupérer des métadonnées pour les types de table utilisé avec les paramètres table.  
  
 Pour plus d’informations sur l’extraction de métadonnées pour les paramètres table, consultez [instruction attributs que les paramètres Affect Table-Valued](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Prise en charge de SQLGetTypeInfo pour les fonctionnalités Date et Heure améliorées  
 Pour les valeurs retournées pour les types de date/heure, consultez [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Pour plus d’informations générales, consultez [améliorations Date / heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Prise en charge SQLGetTypeInfo pour les types CLR volumineux définis par l'utilisateur  
 `SQLGetTypeInfo` prend en charge les grands types CLR définis par l'utilisateur. Pour plus d’informations, consultez [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetTypeInfo Function](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
