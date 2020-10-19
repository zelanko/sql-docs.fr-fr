---
title: Problèmes connus concernant le pilote ODBC sur Linux et macOS
description: Découvrez les problèmes connus avec le pilote Microsoft ODBC pour SQL Server sur Linux et macOS, ainsi que les étapes de résolution des problèmes de connectivité.
ms.date: 09/01/2020
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- known issues
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af611dcc4ca45ae18d650af6248b0f53ab8bcb0b
ms.sourcegitcommit: 9122251ab8bbd46ea3c699e741d6842c995195fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91847299"
---
# <a name="known-issues-for-the-odbc-driver-on-linux-and-macos"></a>Problèmes connus concernant le pilote ODBC sur Linux et macOS

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Cet article contient une liste de problèmes connus avec Microsoft ODBC Driver 13, 13.1 et 17 for SQL Server sur Linux et macOS. Il contient aussi les étapes permettant de résoudre les problèmes de connectivité.

## <a name="known-issues"></a>Problèmes connus

D’autres problèmes seront abordés sur le [blog SQL Server Drivers](https://techcommunity.microsoft.com/t5/SQL-Server/bg-p/SQLServer/label-name/SQLServerDrivers).  

- En raison des limitations de la bibliothèque système, Alpine Linux prend en charge moins de codages de caractères et de paramètres régionaux. Par exemple, en_US.UTF-8 n’est pas disponible. Pour plus d’informations, consultez [musl libc - différences fonctionnelles par rapport à glibc](https://wiki.musl-libc.org/functional-differences-from-glibc.html).

- Windows, Linux et macOS convertissent différemment des caractères de la zone PUA (Private Use Area) ou des caractères EUDC (End User-Defined Characters). Les conversions effectuées sur le serveur dans [!INCLUDE[tsql](../../../includes/tsql-md.md)] utilisent la bibliothèque de conversion Windows. Les conversions dans le pilote utilisent les bibliothèques de conversion Windows, Linux ou macOS. Chaque bibliothèque peut produire des résultats différents lors de l’exécution de ces conversions. Pour plus d’informations, voir [Caractères End-User-Defined et Private Use Area](/windows/desktop/Intl/end-user-defined-characters).

- Si l’encodage client est UTF-8, le gestionnaire de pilotes n’effectue pas toujours une conversion correcte de UTF-8 en UTF-16. Les données sont endommagées quand un ou plusieurs caractères dans la chaîne ne sont pas des caractères UTF-8 valides. Les caractères ASCII sont mappés correctement. Le Gestionnaire de pilotes essaie d’effectuer cette conversion lors de l’appel des versions SQLCHAR de l’API ODBC (par exemple, SQLDriverConnectA). Le gestionnaire de pilotes n’essaie pas d’effectuer cette conversion lors de l’appel des versions SQLWCHAR de l’API ODBC (par exemple, SQLDriverConnectW).  

- Le paramètre *ColumnSize* de **SQLBindParameter** fait référence au nombre de caractères dans le type SQL, tandis que *BufferLength* est le nombre d’octets dans la mémoire tampon de l’application. Toutefois, si le type de données SQL est `varchar(n)` ou `char(n)`, si l’application lie le paramètre en tant que SQL_C_CHAR pour le type C et SQL_CHAR ou SQL_VARCHAR pour le type SQL, et que l’encodage de caractères du client est UTF-8, le pilote peut retourner l’erreur « Troncation à droite de la chaîne de données » même si la valeur de *ColumnSize* est alignée sur la taille du type de données sur le serveur. Cette erreur se produit dans la mesure où les conversions entre les encodages de caractères peuvent changer la longueur des données. Par exemple, un caractère d’apostrophe droite (U+2019) est encodé en CP-1252 comme 0x92 sur un octet, mais en UTF-8 comme séquence 0xe2 0x80 0x99 sur trois octets.

Par exemple, si votre encodage est UTF-8 et que vous spécifiez 1 pour *BufferLength* et *ColumnSize* dans **SQLBindParameter** pour un paramètre de sortie, puis que vous essayez de récupérer le caractère précédent stocké dans une colonne `char(1)` sur le serveur (à l’aide de CP-1252), le pilote tente de le convertir dans l’encodage UTF-8 sur 3 octets, mais ne peut pas faire tenir le résultat dans une mémoire tampon d’un octet. Dans l’autre sens, il compare *ColumnSize* à *BufferLength* dans **SQLBindParameter** avant d’effectuer la conversion entre les différentes pages de codes sur le client et le serveur. Étant donné qu’une *ColumnSize* de 1 est inférieure à une *BufferLength* de 3 (par exemple), le pilote génère une erreur. Pour éviter cette erreur, vérifiez que la longueur des données après la conversion est adaptée à la colonne ou mémoire tampon spécifiée. Notez que *ColumnSize* ne peut pas être supérieure à 8000 pour le type `varchar(n)`.

## <a name="troubleshooting-connection-problems"></a><a id="connectivity"></a> Résolution des problèmes de connexion  

Si vous ne parvenez pas à établir de connexion à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l’aide du pilote ODBC, utilisez les informations suivantes pour identifier le problème.  
  
Le problème de connexion le plus courant est dû à l’installation de deux copies du Gestionnaire de pilotes UnixODBC. Recherchez /usr for libodbc\*.so\*. Si plusieurs versions du fichier apparaissent, vous avez (probablement) plusieurs gestionnaires de pilotes installés. Votre application risque alors d’utiliser la mauvaise version.
  
Activez le journal de connexion en modifiant votre fichier `/etc/odbcinst.ini` afin qu’il contienne la section suivante avec les éléments ci-après :

```
[ODBC]
Trace = Yes
TraceFile = (path to log file, or /dev/stdout to output directly to the terminal)
```  
  
Si vous obtenez un autre échec de connexion et que vous ne voyez pas de fichier journal, il existe (peut-être) deux copies du Gestionnaire de pilotes sur votre ordinateur. Sinon, la sortie du journal doit ressembler à ce qui suit :  
  
```
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 17 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
Si l’encodage de caractères ASCII n’est pas UTF-8, par exemple : 
  
```
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
Il existe plusieurs gestionnaires de pilotes installés et votre application n’utilise pas le bon, ou le gestionnaire de pilotes n’a pas été créé correctement.  
  
Pour plus d’informations sur la résolution des échecs de connexion, consultez :  

- [Procédure de résolution des problèmes de connectivité SQL](/archive/blogs/sql_protocols/steps-to-troubleshoot-sql-connectivity-issues)  
  
- [Résolution des problèmes de connectivité SQL Server 2005 - 1re partie](https://techcommunity.microsoft.com/t5/sql-server/sql-server-2005-connectivity-issue-troubleshoot-part-i/ba-p/383034)  
  
- [Résolution des problèmes de connectivité dans SQL Server 2008 avec le tampon en anneau de connectivité](https://techcommunity.microsoft.com/t5/sql-server/connectivity-troubleshooting-in-sql-server-2008-with-the/ba-p/383393)  
  
- [Résolution des problèmes d’authentification SQL Server](/archive/blogs/sqlsecurity/sql-server-authentication-troubleshooter)  

## <a name="next-steps"></a>Étapes suivantes

Pour obtenir des instructions d’installation du pilote ODBC, consultez les articles suivants :

- [Installation de Microsoft ODBC Driver for SQL Server sur Linux](installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Installation de Microsoft ODBC Driver for SQL Server sur macOS](install-microsoft-odbc-driver-sql-server-macos.md)

Pour plus d’informations, consultez les [instructions de programmation](programming-guidelines.md) et les [notes de publication](release-notes-odbc-sql-server-linux-mac.md).
