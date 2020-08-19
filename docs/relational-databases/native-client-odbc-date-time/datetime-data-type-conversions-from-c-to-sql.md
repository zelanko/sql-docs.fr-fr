---
description: Conversions du type de données datetime de C en SQL
title: Conversions de C en SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC], C to SQL
ms.assetid: 7ac098db-9147-4883-8da9-a58ab24a0d31
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e6fa65cd3bdfd8b6054be31f91eef811d7db4aac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420653"
---
# <a name="datetime-data-type-conversions-from-c-to-sql"></a>Conversions du type de données datetime de C en SQL
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Cette rubrique répertorie les problèmes à prendre en compte lors de la conversion de types C en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types date/heure.  
  
 Les conversions décrites dans le tableau suivant s'appliquent aux conversions effectuées sur le client. Dans les cas où le client spécifie la précision de fraction de seconde pour un paramètre qui diffère de celui défini sur le serveur, la conversion du client peut échouer, mais le serveur retourne une erreur lorsque **SQLExecute** ou **SQLExecuteDirect** est appelé. En particulier, ODBC traite toute troncation des fractions de seconde comme une erreur, tandis que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comportement est d’arrondir ; par exemple, l’arrondi se produit lorsque vous passez de **datetime2 (6)** à **datetime2 (2)**. Les colonnes datetime sont arrondies au 1/300ème de seconde et les secondes des colonnes smalldatetime sont définies avec la valeur zéro (0) par le serveur.  
  
|   | SQL_TYPE_DATE | SQL_TYPE_TIME | SQL_SS_TIME2 | SQL_TYPE_TIMESTAMP | SQL_SS_TIMSTAMPOFFSET | SQL_CHAR | SQL_WCHAR |
| - | ------------- | ------------- | ------------ | ------------------ | --------------------- | -------- | --------- |
| **SQL_C_DATE** |1|-|-|1,6|1,5,6|1,13|1,13|  
| **SQL_C_TIME** |-|1|1|1,7|1, 5, 7|1,13|1,13|  
| **SQL_C_SS_TIME2** |-|1,3|1,10|1,7|1, 5, 7|1,13|1,13|  
| **SQL_C_BINARY(SQL_SS_TIME2_STRUCT)** |N/A|N/A|1,10,11|N/A|N/A|N/A|N/A|  
| **SQL_C_TYPE_TIMESTAMP** |1,2|1,3,4|1,4,10|1,10|1,5,10|1,13|1,13|  
| **SQL_C_SS_TIMESTAMPOFFSET** |1,2,8|1,3,4,8|1,4,8,10|1,8,10|1,10|1,13|1,13|  
| **SQL_C_BINARY(SQL_SS_TIMESTAMPOFFSET_STRUCT)** |N/A|N/A|N/A|N/A|1,10,11|N/A|N/A|  
| **SQL_C_CHAR/SQL_WCHAR (date)** |9|9|9|9,6|9,5,6|N/A|N/A|  
| **SQL_C_CHAR/SQL_WCHAR (time2)** |9|9, 3|9,10|9,7,10|9,5,7,10|N/A|N/A|  
| **SQL_C_CHAR/SQL_WCHAR (datetime)** |9,2|9, 3, 4|9,4,10|9,10|9,5,10|N/A|N/A|  
| **SQL_C_CHAR/SQL_WCHAR (datetimeoffset)** |9,2,8|9, 3, 4, 8|9,4,8,10|9,8,10|9,10|N/A|N/A|  
| **SQL_C_BINARY(SQL_DATE_STRUCT)** |1,11|N/A|N/A|N/A|N/A|N/A|N/A|  
| **SQL_C_BINARY(SQL_TIME_STRUCT)** |N/A|N/A|N/A|N/A|N/A|N/A|N/A|  
| **SQL_C_BINARY(SQL_TIMESTAMP_STRUCT)** |N/A|N/A|N/A|N/A|N/A|N/A|N/A|  
  
## <a name="key-to-symbols"></a>Liste des symboles  
  
-   **-**: Aucune conversion n’est prise en charge. Un enregistrement de diagnostic est généré avec SQLSTATE 07006 et le message « Violation de l'attribut de type de données restreint ».  
  
-   **1**: si les données fournies ne sont pas valides, un enregistrement de diagnostic est généré avec SQLSTATE 22007 et le message « format DateTime non valide ».  
  
-   **2**: les champs d’heure doivent être nuls ou un enregistrement de diagnostic est généré avec SQLSTATE 22008 et le message « troncation fractionnaire ».  
  
-   **3**: les fractions de seconde doivent être égales à zéro ou un enregistrement de diagnostic est généré avec SQLSTATE 22008 et le message « troncation fractionnaire ».  
  
-   **4**: le composant date est ignoré.  
  
-   **5**: le fuseau horaire est défini sur le paramètre de fuseau horaire du client.  
  
-   **6**: l’heure est définie sur zéro.  
  
-   **7**: la date est définie sur la date actuelle.  
  
-   **8**: l’heure est convertie du fuseau horaire du client en heure UTC. Si une erreur se produit pendant cette conversion, un enregistrement de diagnostic est généré avec SQLSTATE 22008 et le message « Dépassement de la capacité du champ datetime ».  
  
-   **9**: la chaîne est analysée et convertie en valeur date, DateTime, DateTimeOffset ou Time, selon le premier caractère de ponctuation rencontré et la présence des composants restants. La chaîne est ensuite convertie en type cible,  selon les règles de la table précédente pour le type source découvert par ce processus. Si une erreur est détectée en analysant les données, un enregistrement de diagnostic est généré avec SQLSTATE 22018 et le message « Valeur de caractère non valide pour la spécification de la casse ». Pour les paramètres datetime et smalldatetime, si l'année est en dehors de la plage prise en charge par ces types, un enregistrement de diagnostic est généré avec SQLSTATE 22007 et le message « Format datetime non valide ».  
  
     Pour datetimeoffset, la valeur doit se situer dans la plage après la conversion au format UTC, même si aucune conversion au format UTC n'est demandée. Cela tient au fait que TDS et le serveur normalisent toujours l'heure des valeurs datetimeoffset pour UTC, si bien que le client doit vérifier que les composants heure se situent dans la plage prise en charge après la conversion au format UTC. Si la valeur n'est pas dans la plage UTC prise en charge, un enregistrement de diagnostic est généré avec SQLSTATE 22007 et le message « Format de datetime non valide ».  
  
-   **10**: si la troncation avec perte de données se produit, un enregistrement de diagnostic est généré avec SQLSTATE 22008 et le message « format d’heure non valide ». Cette erreur se produit également si la valeur est située en dehors de la plage qui peut être représentée par la plage UTC utilisée par le serveur.  
  
-   **11**: si la longueur d’octet des données n’est pas égale à la taille de la structure requise par le type SQL, un enregistrement de diagnostic est généré avec SQLSTATE 22003 et le message « valeur numérique hors limites ».  
  
-   **12**: si la longueur d’octet des données est 4 ou 8, les données sont envoyées au serveur au format smalldatetime ou DateTime TDS brut. Si la longueur d'octet des données correspond exactement à la taille de SQL_TIMESTAMP_STRUCT, les données sont converties au format TDS pour datetime2.  
  
-   **13**: si la troncation avec perte de données se produit, un enregistrement de diagnostic est généré avec SQLSTATE 22001 et le message « données de chaîne, tronqué à droite ».  
  
     Le nombre de chiffres de fractions de seconde (l’échelle) est déterminé à partir de la taille de la colonne de destination, conformément au tableau suivant :  
  
    |   | Échelle impliquée | Échelle impliquée |
    | - | ------------- | ------------- |
    | **Type** | 0 | 1.. 9 |  
    |**SQL_C_TYPE_TIMESTAMP** |19|21..29|  
  
     Toutefois, pour SQL_C_TYPE_TIMESTAMP, si les fractions de seconde peuvent être représentées avec trois chiffres sans perte de données et que la taille de colonne est égale ou supérieure à 23, trois chiffres de fractions de seconde sont générés. Ce comportement garantit la compatibilité descendante pour les applications développées à l'aide de pilotes ODBC plus anciens.  
  
     Pour les tailles de colonne supérieures à la plage du tableau, une échelle de 9 est nécessaire. Cette conversion accepte jusqu'à neuf chiffres de fractions de seconde, valeur maximale autorisée par ODBC.  
  
     Une taille de colonne égale à zéro implique une taille illimitée pour les types de caractères de longueur variable en ODBC (9 chiffres, à moins que la règle des 3 chiffres pour SQL_C_TYPE_TIMESTAMP ne s'applique). La spécification d'une taille de colonne égale à zéro avec un type de caractère de longueur fixe constitue une erreur.  
  
-   Non **applicable : le**comportement existant [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et antérieur est conservé.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations de la date et de l’heure &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
