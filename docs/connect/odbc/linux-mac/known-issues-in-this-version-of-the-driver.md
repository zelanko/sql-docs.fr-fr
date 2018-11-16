---
title: Problèmes connus dans cette Version du pilote pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- known issues
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 15c0402f83dec65b6476d481b77553a037d4fa47
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602029"
---
# <a name="known-issues-in-this-version-of-the-driver"></a>Problèmes connus dans cette version du pilote

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article contient une liste des problèmes connus avec Microsoft ODBC Driver 13, 13.1 et 17 pour SQL Server sur Linux et macOS.

D’autres problèmes seront publiés sur le [blog de l’équipe du pilote Microsoft ODBC](https://blogs.msdn.com/b/sqlnativeclient/).  

- Windows, Linux et macOS convertissent différemment des caractères de la zone PUA (Private Use Area) ou des caractères EUDC (End User-Defined Characters). Les conversions effectuées sur le serveur dans [!INCLUDE[tsql](../../../includes/tsql-md.md)] utilisent la bibliothèque de conversion Windows. Les conversions dans le pilote utilisent les bibliothèques de conversion Windows, Linux ou macOS. Chaque bibliothèque peut produire des résultats différents lors de l’exécution de ces conversions. Pour plus d’informations, voir [Caractères End-User-Defined et Private Use Area](/windows/desktop/Intl/end-user-defined-characters).

- Si le client d’encodage est UTF-8, le Gestionnaire de pilotes ne pas toujours convertit correctement de UTF-8 en UTF-16. Actuellement, une altération des données se produit lorsqu’un ou plusieurs caractères dans la chaîne ne sont pas des caractères UTF-8 valides. Les caractères ASCII sont mappés correctement. Le Gestionnaire de pilotes essaie d’effectuer cette conversion lors de l’appel des versions SQLCHAR de l’API ODBC (par exemple, SQLDriverConnectA). Le gestionnaire de pilotes n’essaie pas d’effectuer cette conversion lors de l’appel des versions SQLWCHAR de l’API ODBC (par exemple, SQLDriverConnectW).  

- Le *ColumnSize* paramètre de **SQLBindParameter** fait référence au nombre de caractères dans le type SQL, tandis que *BufferLength* est le nombre d’octets dans l’application mémoire tampon. Toutefois, si le type de données SQL est `varchar(n)` ou `char(n)`, si l’application lie le paramètre en tant que SQL_C_CHAR ou SQL_C_VARCHAR et que l’encodage de caractères du client est UTF-8, le pilote peut retourner l’erreur « Troncation à droite de la chaîne de données » même si la valeur de *ColumnSize* est alignée sur la taille du type de données sur le serveur. Cette erreur se produit dans la mesure où les conversions entre les encodages de caractères peuvent modifier la longueur des données. Par exemple, une apostrophe droite caractères (U + 2019) est encodé en CP-1252 comme l’octet 0 x 92, mais en UTF-8 en tant que la séquence de 3 octets 0xe2 0x80 0x99.

Par exemple, si votre encodage est UTF-8 et que vous spécifiez 1 pour les deux *BufferLength* et *ColumnSize* dans **SQLBindParameter** pour un paramètre de sortie, puis essaiera à récupérer le caractère précédent est stocké dans un `char(1)` colonne sur le serveur (à l’aide de CP-1252), le pilote tente de convertir de l’encodage UTF-8 3 octets, mais ne peut pas tenir le résultat dans une mémoire tampon sur 1 octet. Dans l’autre sens, il compare *ColumnSize* avec la *BufferLength* dans **SQLBindParameter** avant de procéder à la conversion entre les différentes pages de codes sur le client et serveur. Étant donné qu’une *ColumnSize* de 1 est inférieure à une *BufferLength* de 3 (par exemple), le pilote génère une erreur. Pour éviter cette erreur, vérifiez que la longueur des données après que conversion s’adapte à la mémoire tampon spécifiée ou la colonne. Notez que *ColumnSize* ne peut pas être supérieure à 8000 pour le `varchar(n)` type.

## <a name="see-also"></a> Voir aussi  
[Instructions de programmation](../../../connect/odbc/linux-mac/programming-guidelines.md)  
[Notes de publication](../../../connect/odbc/linux-mac/release-notes.md)  

