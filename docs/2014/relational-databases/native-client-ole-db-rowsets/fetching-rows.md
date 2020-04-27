---
title: Extraction de lignes | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- rowsets [OLE DB], fetching
- IRowset interface
- SQL Server Native Client OLE DB provider, fetching
ms.assetid: 5e6dbe36-b682-464d-adfa-8e886f9bd452
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 21a66754a9259dadcb8788d6afef4947f9a69ad1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63140468"
---
# <a name="fetching-rows"></a>Extraction de lignes
  L’interface **IRowset** est l’interface de base des ensembles de lignes. L’interface **IRowset** fournit des méthodes pour récupérer (fetch) les lignes séquentiellement, obtenir les données de ces lignes et gérer les lignes. Les consommateurs utilisent les méthodes de l’interface **IRowset** pour toutes les opérations de base des ensembles de lignes. Ces opérations incluent l'extraction et la libération des lignes, ainsi que l'obtention des valeurs des colonnes.  
  
 Quand un consommateur obtient un pointeur d’interface sur un ensemble de lignes, la première étape consiste ordinairement à déterminer les fonctions de l’ensemble de lignes à l’aide de la méthode **IRowsetInfo::GetProperties**. Cette opération retourne les informations sur les interfaces exposées par l'ensemble de lignes, ainsi que les fonctions de l'ensemble de lignes n'apparaissant pas comme interfaces distinctes, telles que le nombre maximal de lignes actives et le nombre de lignes qui peuvent avoir simultanément des mises à jour en attente.  
  
 L'étape suivante pour les consommateurs consiste à déterminer les caractéristiques, ou métadonnées, des colonnes de l'ensemble de lignes. À cette fin, ils utilisent la méthode **IColumnsInfo** pour les informations de colonnes simples ou la méthode **IColumnsRowset** pour les informations de colonnes étendues. La méthode **GetColumnInfo** retourne les informations suivantes :  
  
-   Nombre de colonnes de l'ensemble de résultats.  
  
-   Tableau de structures DBCOLUMNINFO, une par colonne.  
  
     L'ordre des structures désigne l'ordre dans lequel les colonnes apparaissent dans l'ensemble de lignes. Chaque structure DBCOLUMNINFO inclut les métadonnées des colonnes, telles que le nom de colonne, le numéro ordinal de la colonne, la longueur maximale d'une valeur de la colonne, le type de données de la colonne, la précision et la longueur.  
  
-   Pointeur vers un stockage de toutes les valeurs de chaîne au sein d'un bloc d'allocation unique.  
  
 Le consommateur détermine s'il a besoin des colonnes des métadonnées ou de celles fondées sur la commande de texte ayant généré l'ensemble de lignes. Il détermine les ordinaux des colonnes nécessaires à partir du classement des informations sur les colonnes retournées par **IColumnsInfo** ou à partir des ordinaux de l’ensemble de lignes des métadonnées des colonnes retournées par **IColumnsRowset**.  
  
 Les interfaces **IColumnsInfo** et **IColumnsRowset** sont utilisées pour extraire des informations sur les colonnes de l’ensemble de lignes. L’interface **IColumnsInfo** retourne un ensemble limité d’informations, alors que l’interface **IColumnsRowset** fournit toutes les métadonnées.  
  
> [!NOTE]  
>  Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 et antérieure, la colonne de métadonnées facultative DBCOLUMN_COMPUTEMODE retournée par **IColumnsInfo::GetColumnsInfo** retourne DBSTATUS_S_ISNULL (au lieu des valeurs indiquant si la colonne est calculée), parce qu’il n’est pas possible de déterminer si la colonne sous-jacente est calculée.  
  
 Les ordinaux sont utilisés pour spécifier une liaison à une colonne. Une liaison est une structure qui associe un élément de la structure du consommateur et une colonne. La liaison peut lier la valeur des données, la longueur et la valeur d'état de la colonne.  
  
 Un jeu de liaisons est regroupé dans un accesseur. Celui-ci est créé à l’aide de la méthode **IAccessor::CreateAccessor**. Un accesseur peut contenir plusieurs liaisons afin que les données de plusieurs colonnes puissent être extraites ou définies en un seul appel. Le consommateur peut créer plusieurs accesseurs pour correspondre aux divers modèles d'utilisation des différentes parties de l'application. Il peut créer et libérer des accesseurs tandis que l'ensemble de lignes continue à exister.  
  
 Pour récupérer (fetch) les lignes de la base de données, le consommateur appelle une méthode, telle que **IRowset::GetNextRows** ou **IRowsetLocate::GetRowsAt**. Ces opérations d'extraction placent les données de ligne du serveur dans le tampon de ligne du fournisseur. Le consommateur ne peut pas accéder directement au tampon de ligne du fournisseur. Le consommateur utilise **IRowset::GetData** pour copier les données de la mémoire tampon du fournisseur vers la mémoire tampon du consommateur, et **IRowsetChange::SetData** pour copier les modifications de données de la mémoire tampon du consommateur vers la mémoire tampon de fournisseur.  
  
 Le consommateur appelle la méthode **GetData** et passe le descripteur à une ligne, le descripteur à un accesseur et un pointeur vers une mémoire tampon allouée par le consommateur. **GetData** convertit les données et retourne les colonnes comme spécifié dans les liaisons utilisées pour créer l’accesseur. Le consommateur peut appeler **GetData** plusieurs fois pour une même ligne, à l’aide de différents accesseurs et mémoires tampon. Par conséquent, le consommateur peut obtenir plusieurs copies des mêmes données.  
  
 Les données de colonnes de longueur variable peuvent être traitées de plusieurs façons. En premier lieu, ces colonnes peuvent être liées à une section limitée de la structure du consommateur. Il s'ensuit une troncation quand la longueur des données dépasse la longueur de la mémoire tampon. Le consommateur peut déterminer que la troncation a eu lieu en vérifiant l'état DBSTATUS_S_TRUNCATED. La longueur retournée est toujours la véritable longueur en octets, afin que le consommateur puisse également déterminer la quantité de données tronquées.  
  
 Quand le consommateur a fini de récupérer ou de mettre à jour les lignes, il les libère avec la méthode **ReleaseRows**. Cela libère les ressources de la copie des lignes de l'ensemble de lignes et crée de la place pour les nouvelles lignes. Le consommateur peut ensuite répéter son cycle d'extraction ou de création de lignes et d'accès à leurs données.  
  
 Lorsque le consommateur en a fini avec l’ensemble de lignes, il appelle la méthode **IAccessor::ReleaseAccessor** pour libérer un accesseur éventuel. Il appelle la méthode **IUnknown::Release** sur toutes les interfaces exposées par l’ensemble de lignes pour libérer l’ensemble de lignes. Lorsque l'ensemble de lignes est libéré, il force la libération des lignes ou accesseurs restants que le consommateur peut détenir.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Prochaine position d'extraction](fetching-rows-next-fetch-position.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](rowsets.md)  
  
  
