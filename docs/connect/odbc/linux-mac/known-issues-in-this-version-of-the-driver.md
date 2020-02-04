---
title: Problèmes connus dans cette version du pilote pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/15/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- known issues
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c3508277502ad7e3eb3b0e7ff048301c8ed1efdd
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "68008781"
---
# <a name="known-issues-in-this-version-of-the-driver"></a>Problèmes connus dans cette version du pilote

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article contient une liste de problèmes connus avec Microsoft ODBC Driver 13, 13.1 et 17 for SQL Server sur Linux et macOS.

D’autres problèmes seront publiés sur le [blog de l’équipe du pilote Microsoft ODBC](https://blogs.msdn.com/b/sqlnativeclient/).  

- Windows, Linux et macOS convertissent différemment des caractères de la zone PUA (Private Use Area) ou des caractères EUDC (End User-Defined Characters). Les conversions effectuées sur le serveur dans [!INCLUDE[tsql](../../../includes/tsql-md.md)] utilisent la bibliothèque de conversion Windows. Les conversions dans le pilote utilisent les bibliothèques de conversion Windows, Linux ou macOS. Chaque bibliothèque peut produire des résultats différents lors de l’exécution de ces conversions. Pour plus d’informations, voir [Caractères End-User-Defined et Private Use Area](/windows/desktop/Intl/end-user-defined-characters).

- Si l’encodage client est UTF-8, le gestionnaire de pilotes n’effectue pas toujours une conversion correcte de UTF-8 en UTF-16. Les données sont endommagées quand un ou plusieurs caractères dans la chaîne ne sont pas des caractères UTF-8 valides. Les caractères ASCII sont mappés correctement. Le Gestionnaire de pilotes essaie d’effectuer cette conversion lors de l’appel des versions SQLCHAR de l’API ODBC (par exemple, SQLDriverConnectA). Le gestionnaire de pilotes n’essaie pas d’effectuer cette conversion lors de l’appel des versions SQLWCHAR de l’API ODBC (par exemple, SQLDriverConnectW).  

- Le paramètre *ColumnSize* de **SQLBindParameter** fait référence au nombre de caractères dans le type SQL, tandis que *BufferLength* est le nombre d’octets dans la mémoire tampon de l’application. Toutefois, si le type de données SQL est `varchar(n)` ou `char(n)`, si l’application lie le paramètre en tant que SQL_C_CHAR ou SQL_C_VARCHAR et que l’encodage de caractères du client est UTF-8, le pilote peut retourner l’erreur « Troncation à droite de la chaîne de données » même si la valeur de *ColumnSize* est alignée sur la taille du type de données sur le serveur. Cette erreur se produit dans la mesure où les conversions entre les encodages de caractères peuvent changer la longueur des données. Par exemple, un caractère d’apostrophe droite (U+2019) est encodé en CP-1252 comme 0x92 sur un octet, mais en UTF-8 comme séquence 0xe2 0x80 0x99 sur trois octets.

Par exemple, si votre encodage est UTF-8 et que vous spécifiez 1 pour *BufferLength* et *ColumnSize* dans **SQLBindParameter** pour un paramètre de sortie, puis que vous essayez de récupérer le caractère précédent stocké dans une colonne `char(1)` sur le serveur (à l’aide de CP-1252), le pilote tente de le convertir dans l’encodage UTF-8 sur 3 octets, mais ne peut pas faire tenir le résultat dans une mémoire tampon d’un octet. Dans l’autre sens, il compare *ColumnSize* à *BufferLength* dans **SQLBindParameter** avant d’effectuer la conversion entre les différentes pages de codes sur le client et le serveur. Étant donné qu’une *ColumnSize* de 1 est inférieure à une *BufferLength* de 3 (par exemple), le pilote génère une erreur. Pour éviter cette erreur, vérifiez que la longueur des données après la conversion est adaptée à la colonne ou mémoire tampon spécifiée. Notez que *ColumnSize* ne peut pas être supérieure à 8000 pour le type `varchar(n)`.

## <a name="see-also"></a>Voir aussi  
[Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[Notes de publication](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  

