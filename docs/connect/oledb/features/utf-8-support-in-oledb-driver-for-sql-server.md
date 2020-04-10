---
title: Prise en charge d’UTF-8 dans le pilote OLE DB pour SQL Server | Microsoft Docs
description: Prise en charge d’UTF-8 dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 12/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: reference
ms.reviewer: v-kaywon
ms.author: v-daenge
author: David-Engel
ms.openlocfilehash: c18870d1d252ba849e11ce0bd040bbce89bd5855
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928279"
---
# <a name="utf-8-support-in-ole-db-driver-for-sql-server"></a>Prise en charge d’UTF-8 dans OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Le pilote Microsoft OLE DB pour SQL Server (version 18.2.1) prend en charge l’encodage de serveur UTF-8. Pour plus d’informations sur la prise en charge UTF-8 SQL Server, voir :
- [Prise en charge d'Unicode et du classement](../../../relational-databases/collations/collation-and-unicode-support.md)
- [Prise en charge d’UTF-8](#ctp23)

> [!IMPORTANT]
> Microsoft OLE DB Driver pour SQL Server utilise la fonction [GetACP](https://docs.microsoft.com/windows/win32/api/winnls/nf-winnls-getacp) pour déterminer l’encodage de la mémoire tampon d’entrée DBTYPE_STR. Les scénarios dans lesquels GetACP renvoie un encodage UTF-8 ne sont pas pris en charge. Si la mémoire tampon doit stocker des données Unicode, le type de données de la mémoire tampon doit être défini sur DBTYPE_WSTR (codé en UTF-16).

## <a name="data-insertion-into-a-utf-8-encoded-char-or-varchar-column"></a>Insertion de données dans une colonne CHAR ou VARCHAR encodée UTF-8
Si vous créez une mémoire tampon de paramètres d’entrée pour l’insertion, elle est décrite à l’aide d’un tableau de [structures DBBINDING](https://go.microsoft.com/fwlink/?linkid=2071182). Chaque structure DBBINDING associe un seul paramètre à la mémoire tampon du consommateur et contient différentes informations, comme la longueur et le type de la valeur de données. Pour une mémoire tampon de paramètres d’entrée de type CHAR, le *wType* de la structure DBBINDING doit être défini sur DBTYPE_STR. Pour une mémoire tampon de paramètres d’entrée de type WCHAR, le *wType* de la structure DBBINDING doit être défini sur DBTYPE_WSTR.

Lorsque vous exécutez une commande comportant des paramètres, le pilote construit les informations de type de données de ces derniers. Si le type de la mémoire tampon d’entrée correspond à celui des données des paramètres, aucune conversion n’est effectuée dans le pilote. Sinon, il convertit la mémoire tampon des paramètres d’entrée dans le type de données des paramètres. L’utilisateur peut définir explicitement le type de données des paramètres en appelant [ICommandWithParameters::SetParameterInfo](https://go.microsoft.com/fwlink/?linkid=2071577). Si cette information n’est pas fournie, le pilote la dérive en (a) récupérant les métadonnées de colonne auprès du serveur lorsque l’instruction est préparée ou (b) en tentant une conversion par défaut à partir du type de données des paramètres d’entrée.

La mémoire tampon des paramètres d’entrée peut être convertie dans le classement de colonne du serveur par le pilote ou par le serveur en fonction du type de données de la mémoire tampon d’entrée et des paramètres. Lors de la conversion, il y a un risque de perte de données si la page de codes du client ou celle du classement de base de données ne peut pas représenter tous les caractères de la mémoire tampon d’entrée. Le tableau suivant décrit le processus de conversion en cas d’insertion de données dans une colonne compatible UTF-8 :

|Type de données de la mémoire tampon|Type de données de paramètre|Conversion|Précaution de l’utilisateur|
|---             |---                |---       |---            |
|DBTYPE_STR|DBTYPE_STR|Conversion de serveur de la page de codes du client à celle du classement de base de données ; conversion de serveur de la page de codes du classement de base de données à celle du classement de colonne.|Vérifiez que la page de codes du client et celle du classement de base de données peuvent représenter tous les caractères des données d’entrée. Par exemple, pour insérer un caractère polonais, la page de codes du client peut être définie sur 1250 (ANSI Europe centrale) ; le classement de base de données peut utiliser le polonais comme indicateur de classement (par exemple, Polish_100_CI_AS_SC) ou être compatible UTF-8.|
|DBTYPE_STR|DBTYPE_WSTR|Conversion de pilote de la page de codes du client à l’encodage UTF-16 ; conversion de serveur de l’encodage UTF-16 à la page de codes du classement de colonne.|Vérifiez que la page de codes du client peut représenter tous les caractères des données d’entrée. Par exemple, pour insérer un caractère polonais, la page de codes du client peut être définie sur 1250 (ANSI Europe centrale).|
|DBTYPE_WSTR|DBTYPE_STR|Conversion de pilote de l’encodage UTF-16 à la page de codes du classement de base de données ; conversion de serveur de la page de codes du classement de base de données à celle du classement de colonne.|Vérifiez que la page du classement de base de données peut représenter tous les caractères des données d’entrée. Par exemple, pour insérer un caractère polonais, la page de codes du classement de base de données peut utiliser le polonais comme indicateur de classement (par exemple, Polish_100_CI_AS_SC) ou être compatible UTF-8.|
|DBTYPE_WSTR|DBTYPE_WSTR|Conversion de serveur de l’encodage UTF-16 à la page de codes du classement de colonne.|Aucun.|

## <a name="data-retrieval-from-a-utf-8-encoded-char-or-varchar-column"></a>Extraction de données à partir d’une colonne CHAR ou VARCHAR encodée UTF-8
Si vous créez une mémoire tampon pour les données récupérées, elle est décrite à l’aide d’un tableau de [structures DBBINDING](https://go.microsoft.com/fwlink/?linkid=2071182). Chaque structure DBBINDING associe une seule colonne dans la ligne récupérée. Pour récupérer les données de la colonne sous forme de CHAR, définissez le *wType* de la structure sur DBBINDING DBTYPE_STR. Pour récupérer les données de la colonne sous forme de WCHAR, définissez le *wType* de la structure sur DBBINDING DBTYPE_WSTR.

Pour l’indicateur de type DBTYPE_STR de la mémoire tampon, le pilote convertit les données encodées UTF-8 dans l’encodage du client. L’utilisateur doit vérifier que cet encodage peut représenter les données de la colonne UTF-8 ; sinon, il y a un risque de perte de données.

Pour l’indicateur de type DBTYPE_WSTR de la mémoire tampon, le pilote convertit les données encodées UTF-8 dans l’encodage UTF-16.

<a name="ctp23"></a>

### <a name="utf-8-support-sql-server-2019-ctp-23"></a>Prise en charge d’UTF-8 (SQL Server 2019 CTP 2.3)

[!INCLUDE[ss2019](../../../includes/sssqlv15-md.md)] introduit la prise en charge complète du codage de caractères UTF-8 courant en tant qu’encodage d’importation ou d’exportation ou que classement de données texte au niveau de la base de données ou des colonnes. UTF-8 est autorisé dans les types de données `CHAR` et `VARCHAR`, et est activé pendant la création du classement d’un objet ou sa modification en un classement avec le suffixe `UTF8`.

Par exemple,`LATIN1_GENERAL_100_CI_AS_SC` en `LATIN1_GENERAL_100_CI_AS_SC_UTF8`. UTF-8 est uniquement disponible pour les classements Windows qui prennent en charge les caractères supplémentaires, comme introduit dans [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. `NCHAR` et `NVARCHAR` autorisent uniquement l’encodage UTF-16 et restent inchangés.

Cette fonctionnalité peut engendrer des économies de stockage importantes, selon le jeu de caractères utilisé. Par exemple, le fait de changer un type de données de colonne existant comportant des chaînes ASCII (Latin) de `NCHAR(10)` en `CHAR(10)` avec un classement prenant en charge UTF-8 se traduit par une réduction de 50 % des besoins en stockage. En effet, `NCHAR(10)` nécessite 20 octets pour le stockage, tandis que `CHAR(10)` nécessite 10 octets pour la même chaîne Unicode.

Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../../../relational-databases/collations/collation-and-unicode-support.md).

Avec **CTP 2.1**, il est maintenant possible de sélectionner le classement UTF-8 par défaut lors de à l’installation de [!INCLUDE[sql-server-2019](../../../includes/sssqlv15-md.md)].

Avec **CTP 2.2**, il est maintenant possible d’utiliser l’encodage de caractères UTF-8 avec la réplication SQL Server.

Avec **CTP 2.3**, il est maintenant possible d’utiliser l’encodage de caractères UTF-8 avec le classement BIN2 (UTF8_BIN2).

## <a name="see-also"></a>Voir aussi  
[Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md) 

[Prise en charge d’UTF-16 dans OLE DB Driver pour SQL Server](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)    
  
  
