---
title: Règles et Limitations des codes XML (SQLXML 4.0) | Microsoft Docs
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
- updategrams [SQLXML], about updategrams
ms.assetid: b5231859-14e2-4276-bc17-db2817b6f235
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ffd38da9c65154ba7bc2af70746416558f8aceea
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150830"
---
# <a name="guidelines-and-limitations-of-xml-updategrams-sqlxml-40"></a>Règles et limitations des codes de mise à jour XML (SQLXML 4.0)
  Tenez compte des éléments suivants lorsque vous utilisez des codes de mise à jour (updategrams) XML :  
  
-   Si vous utilisez une mise à jour pour une opération d’insertion avec uniquement une seule paire de  **\<avant >** et  **\<après >** blocs, les  **\<avant >** bloc peut être omis. À l’inverse, dans le cas d’une opération de suppression, le  **\<après >** bloc peut être omis.  
  
-   Si vous utilisez une mise à jour avec plusieurs  **\<avant >** et  **\<après >** blocs dans le  **\<synchronisation >** de balise, les deux  **\<avant >** blocs et  **\<après >** blocs doivent être spécifiés pour le formulaire  **\<avant >** et  **\<après >** paires.  
  
-   Les mises à jour dans un code de mise à jour sont appliquées à la vue XML fournie avec le schéma XML. Par conséquent, pour que le mappage par défaut soit un succès, vous devez spécifier le nom du fichier de schéma dans le code de mise à jour ou, si le nom de fichier n'est pas fourni, les noms d'élément et d'attribut doivent correspondre aux noms de table et de colonne dans la base de données.  
  
-   SQLXML 4.0 nécessite que toutes les valeurs de colonne dans un code de mise à jour soient explicitement mappées dans le schéma (XDR ou XSD) fourni pour composer la vue XML de ses éléments enfants. Ce comportement diffère des versions antérieures de SQLXML dans lesquelles la valeur d'une colonne non mappée dans le schéma était autorisée si elle appartenait implicitement à la clé étrangère dans une annotation `sql:relationship`. Notez que ce changement n'affecte pas la propagation des valeurs de clé primaire dans les éléments enfants qui a toujours lieu dans SQLXML 4.0 si aucune valeur n'est explicitement spécifiée pour l'élément enfant.  
  
-   Si vous utilisez une mise à jour pour modifier des données dans une colonne binaire (tel que le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `image` type de données), vous devez fournir un schéma de mappage dans lequel le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type de données (par exemple, `sql:datatype="image"`) et le type de données XML (par exemple, `dt:type="binhex"`ou `dt:type="binbase64`) doit être spécifié. Les données de la colonne binaire doivent être spécifiées dans le code de mise à jour ; l'annotation `sql:url-encode` spécifiée dans le schéma de mappage est ignorée par le code de mise à jour.  
  
-   Lorsque vous écrivez un schéma XSD, si la valeur que vous spécifiez pour l'annotation `sql:relation` ou `sql:field` inclut un caractère spécial, tel qu'un espace (par exemple, dans le nom de la table « Détails des commandes »), cette valeur doit apparaître entre crochets (par exemple, « [Détails des commandes] »).  
  
-   Lors de l'utilisation de codes de mise à jour, les relations de chaîne ne sont pas prises en charge. Par exemple, si les tables A et C sont liées par une relation de chaîne qui utilise la table B, l'erreur suivante survient lorsque vous tentez d'exécuter le code de mise à jour :  
  
    ```  
    There is an inconsistency in the schema provided.  
    ```  
  
     Même si le schéma et le code de mise à jour à la fois apparaissent corrects et formés comme il se doit, cette erreur se produira s'il existe une relation de chaîne.  
  
-   Les codes de mise à jour n'autorisent pas le passage de données de type `image` en guise de paramètres lors des mises à jour.  
  
-   Types d’objet binaire volumineux (BLOB) tels que `text/ntext` et images ne doivent pas être utilisés dans le  **\<avant >** bloquer lorsque vous travaillez avec des codes, car cela les inclura pour une utilisation dans le contrôle d’accès concurrentiel. Cela peut entraîner des problèmes avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en raison des limitations sur la comparaison pour les types BLOB. Par exemple, le mot clé LIKE est utilisé dans la clause WHERE pour effectuer une comparaison entre les colonnes du type de données `text` ; toutefois, les comparaisons échouent dans le cas de types BLOB lorsque la taille des données dépasse 8 Ko.  
  
-   Les caractères spéciaux dans les données `ntext` peuvent entraîner des problèmes avec SQLXML 4.0 en raison des limitations sur la comparaison pour les types BLOB. Par exemple, l’utilisation de « [Serializable] » dans le  **\<avant >** bloc d’un codes lorsqu’il est utilisé dans un contrôle d’une colonne de la concurrence `ntext` type échoue avec la description d’erreur SQLOLEDB suivante :  
  
    ```  
    Empty update, no updatable rows found   Transaction aborted  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations de sécurité de mise à jour &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
