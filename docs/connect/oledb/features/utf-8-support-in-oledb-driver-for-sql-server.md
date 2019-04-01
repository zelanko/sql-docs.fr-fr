---
title: Prise en charge d’UTF-8 dans le pilote OLE DB pour SQL Server | Microsoft Docs
description: Prise en charge d’UTF-8 dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: v-kaywon
ms.author: v-kaywon
ms.openlocfilehash: b7f138438d522c9da1b7ef74acbaf963e17d6144
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492601"
---
# <a name="utf-8-support-in-ole-db-driver-for-sql-server"></a>Prise en charge d’UTF-8 dans OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Pilote Microsoft OLE DB pour SQL Server (version 18.2.1) prend en charge l’encodage UTF-8 du serveur. Pour plus d’informations sur la prise en charge de SQL Server UTF-8, consultez :
- [Prise en charge d'Unicode et du classement](../../../relational-databases/collations/collation-and-unicode-support.md)
- [Prise en charge d’UTF-8](../../../sql-server/what-s-new-in-sql-server-ver15.md#utf-8-support-ctp-23)

## <a name="data-insertion-into-a-utf-8-encoded-char-or-varchar-column"></a>Insertion de données dans un format UTF-8 codé colonne CHAR ou VARCHAR
Lorsque vous créez une mémoire tampon de paramètre d’entrée pour l’insertion, la mémoire tampon est décrite à l’aide d’un tableau de [structures DBBINDING](https://go.microsoft.com/fwlink/?linkid=2071182). Chaque structure DBBINDING associe un seul paramètre à la mémoire tampon du consommateur et contient des informations telles que la longueur et le type de la valeur de données. Pour une mémoire tampon d’entrée de paramètre de type CHAR, le *wType* du DBBINDING structure doit être définie sur DBTYPE_STR. Pour une mémoire tampon d’entrée de paramètre de type WCHAR, le *wType* du DBBINDING structure doit être définie sur DBTYPE_WSTR.

Lorsque vous exécutez une commande avec des paramètres, le pilote construit les informations de type de données de paramètre. Si le type de tampon d’entrée et les données du paramètre type de correspondance, aucune conversion n’est effectuée dans le pilote. Sinon, le pilote convertit la mémoire tampon de paramètre d’entrée pour le type de données de paramètre. Le type de données du paramètre peut être défini explicitement par l’utilisateur en appelant [ICommandWithParameters::SetParameterInfo](https://go.microsoft.com/fwlink/?linkid=2071577). Si les informations n’est pas fournies, le pilote dérive les informations de type de données de paramètre en (a) récupération des métadonnées de colonne à partir du serveur lorsque l’instruction est préparée ou (b) tenter une conversion par défaut à partir du type de données de paramètre d’entrée.

La mémoire tampon de paramètre d’entrée peut-être être converti en fonction du classement de colonne de serveur par le pilote ou par le serveur selon le type de données de mémoire tampon d’entrée et le type de données de paramètre. Lors de la conversion, une perte de données peut se produire si la page de codes client ou de la page de codes du classement de base de données ne peut pas représenter tous les caractères dans la mémoire tampon d’entrée. Le tableau suivant décrit le processus de conversion lors de l’insertion de données dans un format UTF-8 activé colonne :

|Type de données de mémoire tampon|Type de données de paramètre|Conversion|Précaution de l’utilisateur|
|---             |---                |---       |---            |
|DBTYPE_STR|DBTYPE_STR|Conversion de serveur à partir de la page de codes client à la page de codes du classement de base de données ; conversion de serveur à partir de la page de codes du classement de base de données à la page de codes de classement de colonne.|Vérifiez la page de codes du client et la page de codes du classement de base de données peuvent représenter tous les caractères dans les données d’entrée. Par exemple, pour insérer un caractère polonais, la page de codes du client peut être affectée de 1250 (ANSI Europe centrale), et le classement de base de données peut utiliser polonais comme indicateur de classement (par exemple, Polish_100_CI_AS_SC) ou être activé en UTF-8.|
|DBTYPE_STR|DBTYPE_WSTR|Conversion de pilote à partir de la page de codes client au format UTF-16 ; conversion de serveur à partir de l’encodage UTF-16 à la page de codes de classement de colonne.|Vérifiez que la page de codes du client peut représenter tous les caractères dans les données d’entrée. Par exemple, pour insérer un caractère polonais, la page de codes du client peut être définie à 1250 (ANSI Europe centrale).|
|DBTYPE_WSTR|DBTYPE_STR|Conversion de pilote à partir de l’encodage UTF-16 à la page de codes du classement de base de données ; conversion de serveur à partir de la page de codes du classement de base de données à la page de codes de classement de colonne.|Vérifiez que la page de codes du classement de base de données peut représenter tous les caractères dans les données d’entrée. Par exemple, pour insérer un caractère polonais, la page de codes du classement de base de données peut utiliser polonais comme indicateur de classement (par exemple, Polish_100_CI_AS_SC) ou être activé en UTF-8.|
|DBTYPE_WSTR|DBTYPE_WSTR|Conversion de serveur à partir de UTF-16 à la page de codes de classement de colonne.|Aucun.|

## <a name="data-retrieval-from-a-utf-8-encoded-char-or-varchar-column"></a>Récupération des données à partir d’un format UTF-8 codé colonne CHAR ou VARCHAR
Lorsque vous créez une mémoire tampon pour les données récupérées, la mémoire tampon est décrite à l’aide d’un tableau de [structures DBBINDING](https://go.microsoft.com/fwlink/?linkid=2071182). Chaque structure DBBINDING associe une seule colonne dans la ligne récupérée. Pour récupérer les données de colonne en tant que CHAR, définissez le *wType* de la structure DBBINDING DBTYPE_STR. Pour récupérer les données de colonne comme WCHAR, définissez le *wType* de la structure DBBINDING DBTYPE_WSTR.

Pour l’indicateur de type mémoire tampon résultat DBTYPE_STR, le pilote convertit les données d’encodé en UTF-8 au client d’encodage. L’utilisateur doit Assurez-vous que le client de codage peut représenter les données à partir de la colonne UTF-8, sinon, une perte de données peut se produire.

Pour l’indicateur de type mémoire tampon résultat DBTYPE_WSTR, le pilote convertit les données au format UTF-8 pour l’encodage UTF-16.
  
## <a name="see-also"></a> Voir aussi  
[Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md) 

[Prise en charge d’UTF-16 dans OLE DB Driver pour SQL Server](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)    
  
  
