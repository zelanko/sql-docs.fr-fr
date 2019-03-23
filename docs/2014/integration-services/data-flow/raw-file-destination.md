---
title: Destination de fichier brut | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledest.f1
helpviewer_keywords:
- append options [Integration Services]
- destinations [Integration Services], Raw File
- raw data [Integration Services]
- writing raw data
- Raw File destination
ms.assetid: d311b458-aefc-4b4d-b1a1-4c0ebbb34214
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b7996ed3cc3ea209361790f23f6955f09be035e4
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385557"
---
# <a name="raw-file-destination"></a>Destination de fichier brut
  La destination de fichier brut écrit des données brutes dans un fichier. Le format des données étant natif pour la destination, les données ne requièrent aucune traduction et peu d'analyse. Cela signifie que la destination de fichier brut peut écrire des données plus rapidement que d'autres destinations telles que les destinations de fichier plat et OLE DB.  
  
 Outre l'écriture de données brutes dans un fichier, vous pouvez également utiliser la destination de fichier brut pour générer un fichier brut vide qui contient uniquement les colonnes (fichier réservé aux métadonnées), sans avoir à exécuter le package. La source de fichier brut vous permet de récupérer les données brutes précédemment écrites par la destination. Vous pouvez également faire pointer la source de fichier brut vers le fichier réservé aux métadonnées.  
  
 Le format de fichier brut contient les informations de tri. La destination de fichier brut enregistre toutes les informations de tri, y compris les indicateurs de comparaison des colonnes de chaîne. La source de fichier brut lit et applique les informations de tri. Vous avez la possibilité de configurer la source de fichier brut pour ignorer les indicateurs de tri du fichier, à l'aide de l'éditeur avancé. Pour plus d’informations sur les indicateurs de comparaison, consultez [Comparaison de données de type chaîne](comparing-string-data.md).  
  
 Vous pouvez configurer la destination de fichier brut de plusieurs manières :  
  
-   Spécifiez un mode d'accès qui est soit le nom du fichier, soit une variable contenant le nom du fichier dans lequel la destination de fichier brut écrit.  
  
-   Indiquez si la destination de fichier brut ajoute des données à un fichier existant qui possède le même nom ou si elle crée un fichier.  
  
 On utilise fréquemment la destination de fichier brut pour écrire des résultats intermédiaires de données partiellement traitées entre des exécutions de packages. Le stockage de données brutes signifie qu'elles peuvent être lues rapidement par une source de fichier brut, puis davantage transformées avant d'être chargées dans leur destination finale. Par exemple, un package peut s'exécuter à plusieurs reprises et à chaque fois écrire des données brutes dans des fichiers. Ultérieurement, un package différent peut utiliser la source de fichier brut pour lire à partir de chaque fichier, utiliser une transformation d'union totale pour fusionner les données en un jeu de données, puis appliquer des transformations supplémentaires qui résument les données avant de les charger dans leur destination finale, telle qu'une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  La destination de fichier brut prend en charge les données nulles mais non les données d'objets BLOB (Binary Large Objects).  
  
> [!NOTE]  
>  La destination de fichier brut n'utilise pas de gestionnaire de connexions.  
  
 Cette source possède une entrée régulière. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="append-and-new-file-options"></a>Options d'ajout et de nouveau fichier  
 La propriété WriteOption inclut des options permettant d’ajouter des données à un fichier existant ou de créer un fichier.  
  
 Le tableau suivant décrit les options disponibles pour la propriété WriteOption.  
  
|Option|Description|  
|------------|-----------------|  
|Ajouter|Ajoute les données à un fichier existant. Les métadonnées des données ajoutées doivent correspondre au format de fichier.|  
|Toujours créer|Crée toujours un nouveau fichier.|  
|Créer une fois|Crée un nouveau fichier. Si le fichier existe, le composant échoue.|  
|Tronquer et ajouter|Tronque un fichier existant, puis écrit les données dans le fichier. Les métadonnées des données ajoutées doivent correspondre au format de fichier.|  
  
 Voici des éléments importants relatifs à l'ajout de données :  
  
-   L'ajout de données à un fichier brut existant n'entraîne pas un nouveau tri des données.  
  
     Vous devez vous assurer que les clés triées restent dans le bon ordre.  
  
-   L'ajout de données à un fichier brut existant n'entraîne pas de modification des métadonnées du fichier (informations de tri).  
  
 Par exemple, un package lit les données triées sur ProductKey (PK). Le flux de données du package ajoute les données à un fichier brut existant. Lors de la première exécution du package, trois lignes sont reçues (PK 1000, 1100, 1200). Le fichier brut contient désormais les données ci-après.  
  
-   1000, productA  
  
-   1100, productB  
  
-   1200, productC  
  
 Lors de la seconde exécution du package, deux nouvelles lignes sont reçues (PK 1001, 1300). Le fichier brut contient désormais les données ci-après.  
  
-   1000, productA  
  
-   1100, productB  
  
-   1200, productC  
  
-   1001, productD  
  
-   1300, productE  
  
 Les nouvelles données sont ajoutées à la fin du fichier brut et les clés triées (PK) ne sont pas ordonnées. Par ailleurs, l’opération d’ajout n’a pas changé les métadonnées du fichier (informations de tri). Si vous lisez le fichier à l'aide de la source de fichier brut, le composant indique que le fichier est toujours trié sur PK même si les données du fichier ne sont plus dans le bon ordre.  
  
 Pour conserver les clés triées dans le bon ordre lors de l'ajout de données, concevez le flux de données du package comme suit :  
  
1.  Récupérez les nouvelles lignes via Source A.  
  
2.  Récupérez les lignes existantes de RawFile1 via Source B.  
  
3.  Combinez les entrées de Source A et Source B à l'aide de la transformation Union All.  
  
4.  Triez sur PK.  
  
5.  Écrivez dans RawFile2 à l'aide de la destination de fichier brut.  
  
     RawFile1 est verrouillé, car il est lu dans le flux de données.  
  
6.  Remplacez RawFile1 par RawFile2.  
  
### <a name="using-the-raw-file-destination-in-a-loop"></a>Utilisation de la destination de fichier brut dans une boucle  
 Si le flux de données qui utilise la destination de fichier brut est dans une boucle, vous pouvez créer le fichier une fois puis ajouter les données au fichier lorsque la boucle se répète. Pour ajouter des données au fichier, les données ajoutées doivent correspondre au format du fichier existant.  
  
 Pour créer le fichier dans la première itération de la boucle puis ajouter des lignes dans les itérations ultérieures de la boucle, procédez comme suit lors de la conception :  
  
1.  Définissez la propriété sur **CreateOnce** ou **CreateAlways**, et effectuez une itération de la boucle. Le fichier est créé. Cette opération permet de s'assurer de la correspondance entre les métadonnées des données ajoutées et le fichier.  
  
2.  Réinitialiser la propriété WriteOption à **Append** et définissez la propriété ValidateExternalMetadata sur `False`.  
  
 Si vous utilisez l’option **TruncateAppend** au lieu de l’option **Append** , celle-ci tronque les lignes ajoutées dans les itérations précédentes, puis ajoute de nouvelles lignes. L’utilisation de l’option **TruncateAppend** nécessite également que les données correspondent au format du fichier.  
  
## <a name="configuration-of-the-raw-file-destination"></a>Configuration de la destination de fichier brut  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../common-properties.md)  
  
-   [Propriétés personnalisées des fichiers bruts](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés du composant, consultez [Définir les propriétés d’un composant de flux de données](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-content"></a>Contenu associé  
 Entrée de blog, [Raw Files Are Awesome](http://www.sqlservercentral.com/blogs/stratesql/archive/2011/1/1/31-days-of-ssis-_1320_-raw-files-are-awesome-_2800_1_2F00_31_2900_.aspx), sur sqlservercentral.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Source de fichier brut](raw-file-source.md)   
 [Flux de données](data-flow.md)  
  
  
