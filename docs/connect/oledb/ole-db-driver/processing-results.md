---
title: Traitement des résultats (pilote OLE DB)
description: Découvrez comment un contrôle serveur consommateur OLE DB Driver pour SQL Server obtient et accède aux données d’un ensemble de lignes produit par une commande ou généré par un fournisseur.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, results processing
- OLE DB, processing results
- rowsets [SQL Server], results processing
- results [OLE DB Driver for SQL Server]
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3cea6c2ef9cfdab250966cbd809be44e6506e4dc
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861532"
---
# <a name="processing-results"></a>Traitement des résultats
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Si un objet d'ensemble de ligne est produit par l'exécution d'une commande ou la génération d'un objet d'ensemble de ligne directement à partir du fournisseur, le consommateur doit extraire et accéder aux données dans l'ensemble de lignes.  
  
 Les ensembles de lignes sont les objets centraux qui permettent à OLE DB Driver pour SQL Server d'exposer des données au format tabulaire. Conceptuellement, un ensemble de lignes est un jeu de lignes dans lequel chaque ligne possède des données de colonne. Un objet d’ensemble de ligne expose des interfaces comme **IRowset** (contient des méthodes pour extraire des lignes de l’ensemble de lignes de manière séquentielle), **IAccessor** (autorise la définition d’un groupe de liaisons de colonnes qui décrivent la manière dont les données tabulaires sont liées aux variables du programme de consommateur), **IColumnsInfo** (fournit des informations sur les colonnes de l’ensemble de lignes) et **IRowsetInfo** (fournit des informations sur l’ensemble de lignes).  
  
 Un consommateur peut appeler la méthode **IRowset::GetData** pour extraire une ligne de données de l’ensemble de lignes dans une mémoire tampon. Avant que **GetData** ne soit appelé, le consommateur décrit la mémoire tampon à l’aide d’un jeu de structures DBBINDING. Chaque liaison décrit la manière dont une colonne dans un ensemble de lignes est stockée dans une mémoire tampon de consommateur et contient les éléments suivants :  
  
-   ordinal de la colonne (ou paramètre) auquel la liaison s'applique ;  
  
-   informations concernant ce qui est lié (par exemple, valeur des données, longueur des données et leur état de liaison) ;  
  
-   informations concernant ce qui est décalé dans la mémoire tampon à chacune de ces parties ;  
  
-   longueur et type des valeurs de données telles qu'elles existent dans la mémoire tampon du consommateur.  
  
 Lors de l'obtention des données, le fournisseur utilise les informations dans chaque liaison afin de déterminer où et comment extraire des données de la mémoire tampon du consommateur. Lors de la définition des données dans la mémoire tampon du consommateur, le fournisseur utilise les informations dans chaque liaison afin de déterminer où et comment retourner des données dans la mémoire tampon du consommateur.  
  
 Une fois les structures DBBINDING spécifiées, un accesseur est créé (**IAccessor::CreateAccessor**). Un accesseur est une collection de liaisons utilisée pour obtenir ou définir les données dans la mémoire tampon du consommateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une application de pilote OLE DB pour SQL Server](../../oledb/ole-db-driver/creating-a-oledb-driver-for-sql-server-application.md)   
 [Rubriques de procédures liées à OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
