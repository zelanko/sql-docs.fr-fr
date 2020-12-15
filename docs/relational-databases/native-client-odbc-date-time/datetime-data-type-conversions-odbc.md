---
title: conversions de type de données DateTime (ODBC) | Microsoft Docs
description: En savoir plus sur les conversions de types de données dans ODBC, qui sont déjà définies par ODBC ou sont des extensions cohérentes d’ODBC.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4876f47266dc0e5053606f9543473f9d283b4470
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97483411"
---
# <a name="datetime-data-type-conversions-odbc"></a>Conversions du type de données datetime (ODBC)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Les conversions suivantes sont déjà définies par ODBC ou constituent une extension cohérente d'ODBC. Les conversions fournies par chaque fournisseur sont déterminées par la communauté servie par le fournisseur, et en conséquence il existe souvent des incohérences entre les fournisseurs. Les valeurs entre crochets ([ et ]) sont facultatives.  
  
-   Le format des chaînes datetime est 'aaaa-mm-jj[ hh:mm:ss[.9999999][ plus/moins hh:mm]]'  
  
-   Le format des chaînes time est 'hh:mm:ss[.9999999]'  
  
-   Le format des chaînes date est 'aaaa-mm-jj'  
  
 Les conversions de chaînes autorisent une souplesse en matière d'espace et de largeur de champ. Pour plus d’informations, consultez la section « formats de données : chaînes et littéraux » de [type de données prise en charge des améliorations de date et d’heure ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  
  
 Les règles suivantes sont les règles générales de conversion :  
  
-   Si aucune heure n'est fournie mais le récepteur peut stocker l'heure, l'heure est définie avec la valeur zéro.  
  
-   Si aucune date n'est présente mais que le récepteur peut stocker la date, la date courante est utilisée.  
  
-   Si aucun fuseau n'est présent dans le type de données que le client utilise mais que le serveur peut stocker le fuseau, la date est stockée dans le fuseau horaire du client. Notez la différence avec le comportement du serveur.  
  
-   Si aucun fuseau n'est présent dans le type de serveur mais que le type de client possède un fuseau, l'heure est convertie en heure UTC avant d'être stockée sur le serveur.  
  
-   Si l'heure est présente mais que le récepteur ne peut pas la stocker, le composant heure est ignoré.  
  
-   Si une date est présente mais que le récepteur ne peut pas la stocker, le composant date est ignoré.  
  
-   Si la troncation de secondes ou de fractions de seconde se produit lors de la conversion de C en SQL, un enregistrement de diagnostic est généré avec la valeur SQLSTATE 22008 et le message « Dépassement de la capacité du champ datetime ».  
  
-   Si la troncation de secondes ou de fractions de seconde se produit lors de la conversion de SQL en C, un enregistrement de diagnostic est généré avec la valeur SQLSTATE 01S07 et le message « Troncation fractionnelle ».  
  
## <a name="in-this-section"></a>Dans cette section  
 [Conversions de C à SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)  
 Répertorie les problèmes à prendre en compte lorsque vous effectuez une conversion de types C en types [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date/time.  
  
 [Conversions de SQL à C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)  
 Répertorie les problèmes à prendre en compte lorsque vous effectuez une conversion de types [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date/time en types C.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations de la date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
