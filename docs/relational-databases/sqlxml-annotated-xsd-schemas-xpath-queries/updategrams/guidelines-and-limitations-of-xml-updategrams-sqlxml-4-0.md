---
title: Instructions et limitations de codes (SQLXML)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9eb717968b191bb7d80f5d68542178bf32734b00
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75241298"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Règles et limitations des codes de mise à jour XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Tenez compte des éléments suivants lorsque vous utilisez des codes de mise à jour (updategrams) XML :  
  
-   Si vous utilisez un mise à jour pour une opération d’insertion avec une seule paire ** \<avant>** et ** \<après>** blocs, le ** \<bloc Before>** peut être omis. Inversement, dans le cas d’une opération de suppression, le ** \<bloc after>** peut être omis.  
  
-   Si vous utilisez un mise à jour avec plusieurs ** \<blocs Before>** et ** \<after>** dans la ** \<balise Sync>** , les deux ** \<avant>** blocks et ** \<after>** blocks doivent être spécifiés pour former ** \<avant>** et ** \<after>** paires.  
  
-   Les mises à jour dans un code de mise à jour sont appliquées à la vue XML fournie avec le schéma XML. Par conséquent, pour que le mappage par défaut soit un succès, vous devez spécifier le nom du fichier de schéma dans le code de mise à jour ou, si le nom de fichier n'est pas fourni, les noms d'élément et d'attribut doivent correspondre aux noms de table et de colonne dans la base de données.  
  
-   SQLXML 4.0 nécessite que toutes les valeurs de colonne dans un code de mise à jour soient explicitement mappées dans le schéma (XDR ou XSD) fourni pour composer la vue XML de ses éléments enfants. Ce comportement diffère des versions antérieures de SQLXML, qui permettaient la création d’une valeur pour une colonne non mappée dans le schéma si elle était implicite dans le cadre de la clé étrangère dans une annotation **SQL : Relationship** . Notez que ce changement n'affecte pas la propagation des valeurs de clé primaire dans les éléments enfants qui a toujours lieu dans SQLXML 4.0 si aucune valeur n'est explicitement spécifiée pour l'élément enfant.  
  
-   Si vous utilisez un mise à jour pour modifier des données dans une colonne binaire (telle que le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type de données **image** ), vous devez fournir un schéma de mappage dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lequel le type de données (par exemple, **SQL : datatype = "image"**) et le type de données XML (par exemple, **DT : type = "BinHex"** ou **DT : type = "BinBase64**) doivent être spécifiés. Les données de la colonne binaire doivent être spécifiées dans le mise à jour ; l’annotation **SQL : URL-Encode** qui est spécifiée dans le schéma de mappage est ignorée par mise à jour.  
  
-   Lorsque vous écrivez un schéma XSD, si la valeur que vous spécifiez pour l’annotation **SQL : relation** ou **SQL : Field** comprend un caractère spécial, tel qu’un espace (par exemple, dans le nom de la table « Order Details »), cette valeur doit être mise entre crochets (par exemple, « [Order Details] »).  
  
-   Lors de l'utilisation de codes de mise à jour, les relations de chaîne ne sont pas prises en charge. Par exemple, si les tables A et C sont liées par une relation de chaîne qui utilise la table B, l'erreur suivante survient lorsque vous tentez d'exécuter le code de mise à jour :  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Même si le schéma et le code de mise à jour à la fois apparaissent corrects et formés comme il se doit, cette erreur se produira s'il existe une relation de chaîne.  
  
-   Les codes n’autorisent pas le passage de données de type **image** comme paramètres lors des mises à jour.  
  
-   Les types d’objets BLOB (Binary Large Object) tels que **text/ntext** et images ne doivent pas être utilisés dans le bloc ** \<Before>** dans lors de l’utilisation de codes, car cela les inclura pour une utilisation dans le contrôle d’accès concurrentiel. Cela peut entraîner des problèmes avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en raison des limitations sur la comparaison pour les types BLOB. Par exemple, le mot clé LIKE est utilisé dans la clause WHERE pour la comparaison entre les colonnes du type de données **Text** ; Toutefois, les comparaisons échouent dans le cas de types d’objets BLOB où la taille des données est supérieure à 8 Ko.  
  
-   Les caractères spéciaux dans les données **ntext** peuvent engendrer des problèmes avec SQLXML 4,0 en raison des limitations de comparaison pour les types d’objets BLOB. Par exemple, l’utilisation de « [Serializable] » dans le bloc ** \<Before>** d’un codes lorsqu’il est utilisé dans le contrôle d’accès concurrentiel d’une colonne de type **ntext** échouera avec la description d’erreur SQLOLEDB suivante :  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
