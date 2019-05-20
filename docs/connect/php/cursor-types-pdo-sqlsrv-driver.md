---
title: Types de curseurs (pilote PDO_SQLSRV) | Microsoft Docs
ms.custom: ''
ms.date: 05/03/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa270574d55d50e3b2d8653273027e9d5f133766
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65099739"
---
# <a name="cursor-types-pdosqlsrv-driver"></a>Types de curseurs (pilote PDO_SQLSRV)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Le pilote PDO_SQLSRV vous permet de créer des jeux de résultats à défilement avec l’un des différents curseurs disponibles.

Pour plus d’informations sur la façon de spécifier un curseur à l’aide du pilote PDO_SQLSRV et pour obtenir des exemples de code, consultez [PDO::prepare](../../connect/php/pdo-prepare.md).

## <a name="pdosqlsrv-and-server-side-cursors"></a>PDO_SQLSRV et les curseurs côté serveur
Avant la version 3.0 du [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], le pilote PDO_SQLSRV vous permettait de créer un jeu de résultats avec un curseur avant uniquement ou statique côté serveur. À compter de la version 3.0 du [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], les curseurs dynamiques et de jeu de clés sont également disponibles.

Vous pouvez indiquer le type de curseur côté serveur à l’aide de [PDO::prepare](../../connect/php/pdo-prepare.md) pour sélectionner l’un des types de curseurs suivants :

-   `PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY`

-   `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`

Vous pouvez demander un curseur dynamique, statique ou de jeu de clés en spécifiant `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`, puis en passant la valeur appropriée à `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE`. Les valeurs que vous pouvez passer à `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE` pour les curseurs côté serveur sont :

-   `PDO::SQLSRV_CURSOR_DYNAMIC`

-   `PDO::SQLSRV_CURSOR_STATIC`

-   `PDO::SQLSRV_CURSOR_KEYSET`

## <a name="pdosqlsrv-and-client-side-cursors"></a>PDO_SQLSRV et les curseurs côté client
Les curseurs côté client ont été ajoutés dans la version 3.0 du [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], et vous permettent de mettre en cache un jeu de résultats entier en mémoire. L’un des avantages est que le nombre de lignes est disponible après l’exécution d’une requête.

Les curseurs côté client doivent être utilisés pour les jeux de résultats petits à moyens. Les grands jeux de résultats doivent utiliser des curseurs côté serveur.

Une requête retourne false si la mémoire tampon n’est pas assez grande pour contenir un jeu de résultats entier quand vous utilisez un curseur côté client. Vous pouvez augmenter la taille de la mémoire tampon jusqu’à la limite de mémoire PHP.

Vous pouvez configurer la taille de la mémoire tampon contenant le jeu de résultats avec l’attribut `PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE` de [PDO::setAttribute](../../connect/php/pdo-setattribute.md) ou [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md). Vous pouvez également définir la taille maximale de la mémoire tampon dans le fichier php.ini avec pdo_sqlsrv.client_buffer_max_kb_size (par exemple, pdo_sqlsrv.client_buffer_max_kb_size = 1024).

Vous pouvez demander un curseur côté client à l’aide de [PDO::prepare](../../connect/php/pdo-prepare.md), en spécifiant le type de curseur `PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`, puis en spécifiant `PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED`.

## <a name="example"></a> Exemple
L’exemple suivant montre comment spécifier un curseur mis en mémoire tampon.
```
<?php
$database = "AdventureWorks";
$server = "(local)";
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");

$query = "select * from Person.ContactType";
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED));
$stmt->execute();
print $stmt->rowCount();

echo "\n";

while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){
   print "$row[Name]\n";
}
echo "\n..\n";

$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );
print_r($row);

$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );
print "$row[Name]\n";

$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );
print "$row[1]\n";

$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );
print "$row[1]..\n";

$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );
print_r($row);

$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );
print_r($row);
?>
```

## <a name="see-also"></a> Voir aussi
[Spécification d’un type de curseur et sélection de lignes](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)

