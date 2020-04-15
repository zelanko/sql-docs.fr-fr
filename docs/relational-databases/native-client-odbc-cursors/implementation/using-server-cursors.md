---
title: Utilisation de Cursors Serveur (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, cursors
- cursors [ODBC], server cursors
- ODBC cursors, server cursors
- server cursors [SQL Server]
ms.assetid: 8a6d99b7-10b8-4474-8639-4914b25ba170
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ede31d9d59ef7d01dfd7e7b610edae273cbc5d64
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305376"
---
# <a name="using-server-cursors"></a>Utilisation des curseurs côté serveur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Si une application ODBC définit l’un des attributs du curseur ODBC à autre chose que les défauts, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chauffeur native ODBC demande au serveur de implémenter un curseur serveur API du même type. L'utilisation de curseurs côté serveur d'API libère la mémoire sur le client et peut réduire considérablement le trafic réseau entre le client et le serveur.  
  
 Un inconvénient possible des curseurs côté serveur d'API est qu'ils ne prennent pas en charge toutes les instructions SQL. Les curseurs côté serveur d'API ne peuvent pas être utilisés pour exécuter :  
  
-   Les lots ou les procédures stockées qui retournent plusieurs ensembles de résultats.  
  
-   Les instructions SELECT contenant les clauses COMPUTE, COMPUTE BY, FOR BROWSE ou INTO.  
  
-   Une instruction EXECUTE faisant référence à une procédure stockée distante.  
  
 En cas de connexion à une instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'exécution d'une instruction avec ces caractéristiques à l'aide d'un curseur côté serveur provoque la conversion du curseur en un jeu de résultats par défaut. En cas de connexion aux versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il s'ensuit une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les curseurs sont implémentés](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
