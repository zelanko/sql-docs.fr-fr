---
title: À l’aide de la Classification des données avec Microsoft ODBC Driver pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: v-makouz
ms.author: v-makouz
manager: kenvh
ms.openlocfilehash: 0d010bcfc74011cb0e7e2864aeff97e65bf16203
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62637442"
---
# <a name="data-classification"></a>Classification des données
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>Vue d’ensemble
Pour les besoins de la gestion des données sensibles, SQL Server et Azure SQL Server a introduit la possibilité de fournir des colonnes de la base de données avec des métadonnées de sensibilité qui permet à l’application cliente pour gérer différents types de données sensibles (telles que le contrôle d’intégrité, financière, etc. ) conformément aux stratégies de protection des données.

Pour plus d’informations sur la façon d’affecter la classification à des colonnes, consultez [découverte de données SQL et la Classification](https://docs.microsoft.com/sql/relational-databases/security/sql-data-discovery-and-classification?view=sql-server-2017).

Microsoft ODBC Driver 17.2 permet la récupération de ces métadonnées via SQLGetDescField à l’aide de l’identificateur de champ SQL_CA_SS_DATA_CLASSIFICATION.

## <a name="format"></a>Format
SQLGetDescField présente la syntaxe suivante :

```  
SQLRETURN SQLGetDescField(  
     SQLHDESC        DescriptorHandle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     FieldIdentifier,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```
*DescriptorHandle*  
 [Entrée] Handle IRD (descripteur de ligne d’implémentation). Peut être récupéré par un appel à SQLGetStmtAttr avec l’attribut d’instruction SQL_ATTR_IMP_ROW_DESC
  
 *RecNumber*  
 [Entrée] 0
  
 *FieldIdentifier*  
 [Entrée] SQL_CA_SS_DATA_CLASSIFICATION
  
 *ValuePtr*  
 [Sortie] Mémoire tampon de sortie
  
 *BufferLength*  
 [Entrée] Longueur de la mémoire tampon de sortie en octets

 *StringLengthPtr* pointeur [sortie] vers la mémoire tampon dans lequel retourner le nombre total d’octets à retourner dans *ValuePtr*.
 
> [!NOTE]
> Si la taille de la mémoire tampon est inconnue, il peut être déterminé en appelant SQLGetDescField avec *ValuePtr* en tant que valeur NULL et en examinant la valeur de *StringLengthPtr*.
 
Si les informations de Classification des données ne sont pas disponibles, un *champ de descripteur non valide* erreur est renvoyée.

Lors d’un appel réussi à SQLGetDescField, la mémoire tampon vers laquelle pointe *ValuePtr* contiendra les données suivantes :

 `nn nn [n sensitivitylabels] tt tt [t informationtypes] cc cc [c columnsensitivitys]`

> [!NOTE]
> `nn nn`, `tt tt`, et `cc cc` sont des entiers multioctets, qui sont stockées avec l’octet le moins significatif à l’adresse la plus basse.

*`sensitivitylabel`* et *`informationtype`* sont tous deux du formulaire

 `nn [n bytes name] ii [i bytes id]`

*`columnsensitivity`* est au format

 `nn nn [n sensitivityprops]`

Pour chaque colonne *(c)* , *n* 4 octets *`sensitivityprops`* sont présents :

 `ss ss tt tt`

s - index dans le *`sensitivitylabels`* tableau, `FF FF` si ne pas d’étiquette

t - l’index dans le *`informationtypes`* tableau, `FF FF` si ne pas d’étiquette


<br><br>
Le format des données peut être exprimé en tant que les structures de pseudo suivants :

```
struct IDnamePair {
 BYTE nameLen;
 USHORT name[nameLen];
 BYTE idLen;
 USHORT id[idLen];
};

struct SensitivityProp {
 USHORT labelIdx;
 USHORT infoTypeIdx;
};

USHORT nLabels;
struct IDnamePair labels[nLabels];
USHORT nInfoTypes;
struct IDnamePair infotypes[nInfoTypes];
USHORT nColumns;
struct {
 USHORT nProps;
 struct SensitivityProp[nProps];
} columnClassification[nColumns];
```


## <a name="code-sample"></a>Exemple de code
Tester l’application qui illustre comment lire les métadonnées de Classification des données. Sur Windows il peut être compilé à l’aide de `cl /MD dataclassification.c /I (directory of msodbcsql.h) /link odbc32.lib` et exécuter avec une chaîne de connexion et une requête SQL (que retourne colonnes classifiées) en tant que paramètres :

```
#ifdef _WIN32
#include <windows.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include <msodbcsql.h>
#include <stdio.h>
SQLHANDLE env, dbc, stmt;
void checkRC_exit(SQLRETURN rc, SQLHANDLE hand, SQLSMALLINT htype, int retcode, char *action)
{
    if ((rc == SQL_ERROR || rc == SQL_SUCCESS_WITH_INFO) && hand)
    {
        char msg[1024], state[6];
        int i = 0;
        SQLRETURN rc2;
        SQLINTEGER err;
        SQLSMALLINT lenout;
        while ((rc2 = SQLGetDiagRec(htype, hand, ++i, state, &err, msg, sizeof(msg), &lenout)) == SQL_SUCCESS ||
            rc2 == SQL_SUCCESS_WITH_INFO)
            printf("%d (%d)[%s]%s\n", i, err, state, msg);
    }
    if (rc == SQL_ERROR && retcode)
    {
        printf("Error occurred%s%s\n", action ? " upon " : "", action ? action : "");
        exit(retcode);
    }
}
void printLabelInfo(char *type, char **pptr)
{
    char *ptr = *pptr;
    unsigned short nlabels;
    printf("----- %s(%u) -----\n", type, nlabels = *(unsigned short*)ptr);
    ptr += sizeof(unsigned short);
    while (nlabels--)
    {
        int namelen, idlen;
        char *nameptr, *idptr;
        namelen = *ptr++;
        nameptr = ptr;
        ptr += namelen * 2;
        idlen = *ptr++;
        idptr = ptr;
        ptr += idlen * 2;
        wprintf(L"Name: \"%.*s\" Id: \"%.*s\"\n", namelen, nameptr, idlen, idptr);
    }
    *pptr = ptr;
}
int main(int argc, char **argv)
{
    unsigned char *dcbuf;
    unsigned int dclen = 0;
    SQLRETURN rc;
    SQLHANDLE ird;
    if (argc < 3)
    {
        fprintf(stderr, "usage: dataclassification connstr query\n");
        return 1;
    }
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_ENV, 0, &env), 0, 0,
        2, "allocate environment");
    checkRC_exit(SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0), env, SQL_HANDLE_ENV,
        3, "set ODBC version");
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc), env, SQL_HANDLE_ENV,
        4, "allocate connection");
    checkRC_exit(SQLDriverConnect(dbc, 0, argv[1], SQL_NTS, 0, 0, 0, SQL_DRIVER_NOPROMPT), dbc, SQL_HANDLE_DBC,
        5, "connect to server");
    checkRC_exit(SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt), dbc, SQL_HANDLE_DBC,
        6, "allocate statement");
    checkRC_exit(SQLExecDirect(stmt, argv[2], SQL_NTS), stmt, SQL_HANDLE_STMT,
        7, "execute query");
    checkRC_exit(SQLGetStmtAttr(stmt, SQL_ATTR_IMP_ROW_DESC, (SQLPOINTER)&ird, SQL_IS_POINTER, 0), stmt, SQL_HANDLE_STMT,
        8, "get IRD handle");
    rc = SQLGetDescFieldW(ird, 0, SQL_CA_SS_DATA_CLASSIFICATION, dcbuf, 0, &dclen);
    if (rc != SQL_SUCCESS && rc != SQL_SUCCESS_WITH_INFO)
    {
        checkRC_exit(rc, ird, SQL_HANDLE_DESC, 0, 0);
        printf("Error reading SQL_CA_SS_DATA_CLASSIFICATION IRD field. Ensure that the driver and\n"
            "server both support the Data Classification feature, and that the query returns columns\n"
            "with classification information.\n");
    }
    else
    {
        SQLINTEGER dclenout;
        unsigned char *dcptr;
        unsigned short ncols;
        printf("Data Classification information (%u bytes):\n", dclen);
        if (!(dcbuf = malloc(dclen)))
        {
            printf("Memory Allocation Error");
            return 9;
        }
        checkRC_exit(SQLGetDescFieldW(ird, 0, SQL_CA_SS_DATA_CLASSIFICATION, dcbuf, dclen, &dclenout),
            ird, SQL_HANDLE_DESC, 10, "reading SQL_CA_SS_DATA_CLASSIFICATION");
        dcptr = dcbuf;
        printLabelInfo("Labels", &dcptr);
        printLabelInfo("Information Types", &dcptr);
        printf("----- Column Sensitivities(%u) -----\n", ncols = *(unsigned short*)dcptr);
        dcptr += sizeof(unsigned short);
        while (ncols--)
        {
            unsigned short nprops = *(unsigned short*)dcptr;
            dcptr += sizeof(unsigned short);
            while (nprops--)
            {
                unsigned short labelidx, typeidx;
                labelidx = *(unsigned short*)dcptr; dcptr += sizeof(unsigned short);
                typeidx = *(unsigned short*)dcptr; dcptr += sizeof(unsigned short);
                printf(labelidx == 0xFFFF ? "(none) " : "%u ", labelidx);
                printf(typeidx == 0xFFFF ? "(none)\n" : "%u\n", typeidx);
            }
            printf("-----\n");
        }
        if (dcptr != dcbuf + dclen)
        {
            printf("Error: unexpected parse of DATACLASSIFICATION data\n");
            return 11;
        }
        free(dcbuf);
    }
    return 0;
}
```

