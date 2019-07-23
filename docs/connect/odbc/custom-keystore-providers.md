---
title: Fournisseurs de magasins de clés personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a6166d7d-ef34-4f87-bd1b-838d3ca59ae7
ms.author: v-chojas
author: MightyPen
ms.openlocfilehash: 0cf2946517be732094d01ff9889faf080a36e85b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006494"
---
# <a name="custom-keystore-providers"></a>Fournisseurs de magasins de clés personnalisés
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>Vue d’ensemble

La fonctionnalité de chiffrement de colonne de SQL Server 2016 requiert que les clés de chiffrement de colonne chiffrées (ECEKs) stockées sur le serveur soient récupérées par le client, puis déchiffrées en clés de chiffrement de colonne (clés CEK) afin d’accéder aux données stockées dans des colonnes chiffrées. Les ECEKs sont chiffrés par les clés principales de colonne (clés CMK), et la sécurité du CMK est importante pour la sécurité du chiffrement de colonne. Ainsi, le CMK doit être stocké dans un emplacement sécurisé. l’objectif d’un fournisseur de magasins de clés de chiffrement de colonne consiste à fournir une interface pour permettre au pilote ODBC d’accéder à ces clés CMK stockés en toute sécurité. Pour les utilisateurs disposant de leur propre stockage sécurisé, l’interface du fournisseur de magasin de clés personnalisé fournit une infrastructure pour implémenter l’accès au stockage sécurisé des CMK pour le pilote ODBC, qui peut ensuite être utilisé pour effectuer le chiffrement et le déchiffrement clé CEK.

Chaque fournisseur de magasin de clés contient et gère un ou plusieurs clés CMK, qui sont identifiés par des chemins d’accès de clé-chaînes d’un format défini par le fournisseur. Cela, avec l’algorithme de chiffrement, également une chaîne définie par le fournisseur, peut être utilisé pour effectuer le chiffrement d’un clé CEK et le déchiffrement d’un ECEK. L’algorithme, ainsi que le ECEK et le nom du fournisseur, sont stockés dans les métadonnées de chiffrement de la base de données. Pour plus d’informations, consultez [créer une clé principale de colonne](../../t-sql/statements/create-column-master-key-transact-sql.md) et créer une clé de chiffrement de [colonne](../../t-sql/statements/create-column-encryption-key-transact-sql.md) . Ainsi, les deux opérations fondamentales de la gestion des clés sont les suivantes:

```
CEK = DecryptViaCEKeystoreProvider(CEKeystoreProvider_name, Key_path, Key_algorithm, ECEK)

-and-

ECEK = EncryptViaCEKeystoreProvider(CEKeyStoreProvider_name, Key_path, Key_algorithm, CEK)
```

`CEKeystoreProvider_name` où est utilisé pour identifier le fournisseur de magasin de clés de chiffrement de colonne spécifique (CEKeystoreProvider), et les autres arguments sont utilisés par le CEKeystoreProvider pour chiffrer/déchiffrer le (E) clé CEK. Le nom et le chemin d’accès au keyPath sont fournis par les métadonnées CMK, tandis que les valeurs algorithmes et ECEK sont fournies par les métadonnées clé CEK. Plusieurs fournisseurs de magasin de clés peuvent être présents avec le ou les fournisseurs intégrés par défaut. Lors de l’exécution d’une opération qui requiert clé CEK, le pilote utilise les métadonnées CMK pour rechercher le fournisseur de magasin de clés approprié par nom et exécute son opération de déchiffrement, qui peut être exprimée comme suit:

```
CEK = CEKeyStoreProvider_specific_decrypt(Key_path, Key_algorithm, ECEK)
```

Bien que le pilote n’ait pas besoin de chiffrer clés CEK, un outil de gestion de clés peut avoir besoin de le faire pour mettre en œuvre des opérations telles que la création et la rotation CMK. pour cela, vous devez effectuer l’opération inverse:

```
ECEK = CEKeyStoreProvider_specific_encrypt(Key_path, Key_algorithm, CEK)
```

### <a name="cekeystoreprovider-interface"></a>Interface CEKeyStoreProvider

Ce document décrit en détail l’interface CEKeyStoreProvider. Un fournisseur de magasin de clés qui implémente cette interface peut être utilisé par le Microsoft ODBC Driver for SQL Server. Les implémenteurs CEKeyStoreProvider peuvent utiliser ce guide pour développer des fournisseurs de magasins de clés personnalisés utilisables par le pilote.

Une bibliothèque de fournisseurs de magasin de clés («bibliothèque de fournisseurs») est une bibliothèque de liens dynamiques qui peut être chargée par le pilote ODBC et contient un ou plusieurs fournisseurs de magasin de clés. Le symbole `CEKeystoreProvider` doit être exporté par une bibliothèque de fournisseur et être l’adresse d’un tableau de pointeurs `CEKeystoreProvider` se terminant par un caractère NULL dans les structures, un pour chaque fournisseur de magasin de clés dans la bibliothèque.

Une `CEKeystoreProvider` structure définit les points d’entrée d’un fournisseur de magasin de clés unique:

```
typedef struct CEKeystoreProvider {
    wchar_t *Name;
    int (*Init)(CEKEYSTORECONTEXT *ctx, errFunc *onError);
    int (*Read)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int *len);
    int (*Write)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len);
    int (*DecryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *ecek,
                        unsigned short ecekLen,
                        unsigned char **cekOut,
                        unsigned short *cekLen);
    int (*EncryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *cek,
                        unsigned short cekLen,
                        unsigned char **ecekOut,
                        unsigned short *ecekLen);
    void (*Free)();
} CEKEYSTOREPROVIDER;
```

|Nom du champ|Description|
|:--|:--|
|`Name`|Nom du fournisseur de magasin de clés. Il ne doit pas être identique à un autre fournisseur de magasin de clés précédemment chargé par le pilote ou présent dans cette bibliothèque. Chaîne à caractères larges* se terminant par le caractère Null.|
|`Init`|Fonction d’initialisation. Si aucune fonction d’initialisation n’est requise, ce champ peut avoir la valeur null.|
|`Read`|Fonction de lecture du fournisseur. Peut avoir la valeur null s’il n’est pas obligatoire.|
|`Write`|Fonction d’écriture du fournisseur. Obligatoire si Read n’a pas la valeur null. Peut avoir la valeur null s’il n’est pas obligatoire.|
|`DecryptCEK`|Fonction de déchiffrement ECEK. Cette fonction est la raison de l’existence d’un fournisseur de magasin de clés et ne doit pas être null.|
|`EncryptCEK`|Fonction de chiffrement clé CEK. Le pilote n’appelle pas cette fonction, mais il est fourni pour permettre l’accès par programme à la création de ECEK par les outils de gestion de clés. Peut avoir la valeur null s’il n’est pas obligatoire.|
|`Free`|Fonction d’arrêt. Peut avoir la valeur null s’il n’est pas obligatoire.|

À l’exception de Free, les fonctions de cette interface ont toutes une paire de paramètres, **CTX** et **OnError**. La première identifie le contexte dans lequel la fonction est appelée, tandis que la dernière est utilisée pour signaler les erreurs. Pour plus d’informations, consultez [contextes](#context-association) et [gestion des erreurs](#error-handling) ci-dessous.

```
int Init(CEKEYSTORECONTEXT *ctx, errFunc onError);
```
Nom de l’espace réservé pour une fonction d’initialisation définie par le fournisseur. Le pilote appelle cette fonction une fois, une fois qu’un fournisseur a été chargé, mais avant la première fois, il en a besoin pour effectuer le déchiffrement de ECEK ou les demandes de lecture ()/Write (). Utilisez cette fonction pour effectuer l’initialisation dont elle a besoin. 

|Argument|Description|
|:--|:--|
|`ctx`|Entrée Contexte de l’opération.|
|`onError`|Entrée Fonction de rapport d’erreurs.|
|`Return Value`|Retourne une valeur différente de zéro pour indiquer la réussite, ou zéro pour indiquer un échec.|

```
int Read(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int *len);
```

Nom de l’espace réservé pour une fonction de communication définie par le fournisseur. Le pilote appelle cette fonction lorsque l’application demande de lire des données à partir d’un fournisseur (précédemment écrit) à l’aide de l’attribut de connexion SQL_COPT_SS_CEKEYSTOREDATA, ce qui permet à l’application de lire des données arbitraires du fournisseur. Pour plus d’informations, consultez [communication avec les fournisseurs de magasin de clés](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) .

|Argument|Description|
|:--|:--|
|`ctx`|Entrée Contexte de l’opération.|
|`onError`|Entrée Fonction de rapport d’erreurs.|
|`data`|Sortie Pointeur vers une mémoire tampon dans laquelle le fournisseur écrit des données à lire par l’application. Cela correspond au champ de données de la structure CEKEYSTOREDATA.|
|`len`|INOUT Pointeur vers une valeur de longueur; lors de l’entrée, il s’agit de la longueur maximale de la mémoire tampon de données, et le fournisseur ne doit pas écrire plus de * Len octets. Lors du retour, le fournisseur doit mettre à jour * Len avec le nombre d’octets réellement écrits.|
|`Return Value`|Retourne une valeur différente de zéro pour indiquer la réussite, ou zéro pour indiquer un échec.|

```
int Write(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int len);
```
Nom de l’espace réservé pour une fonction de communication définie par le fournisseur. Le pilote appelle cette fonction lorsque l’application demande à écrire des données dans un fournisseur à l’aide de l’attribut de connexion SQL_COPT_SS_CEKEYSTOREDATA, ce qui permet à l’application d’écrire des données arbitraires sur le fournisseur. Pour plus d’informations, consultez [communication avec les fournisseurs de magasin de clés](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) .

|Argument|Description|
|:--|:--|
|`ctx`|Entrée Contexte de l’opération.|
|`onError`|Entrée Fonction de rapport d’erreurs.|
|`data`|Entrée Pointeur vers une mémoire tampon contenant les données que le fournisseur doit lire. Cela correspond au champ de données de la structure CEKEYSTOREDATA. Le fournisseur ne doit pas lire plus de Len octets à partir de cette mémoire tampon.|
|`len`|Entrée Nombre d’octets disponibles dans les données. Cela correspond au champ dataSize de la structure CEKEYSTOREDATA.|
|`Return Value`|Retourne une valeur différente de zéro pour indiquer la réussite, ou zéro pour indiquer un échec.|

```
int (*DecryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen);
```
Nom de l’espace réservé pour une fonction de déchiffrement ECEK définie par le fournisseur. Le pilote appelle cette fonction pour déchiffrer un ECEK chiffré par un CMK associé à ce fournisseur dans un clé CEK.

|Argument|Description|
|:--|:--|
|`ctx`|Entrée Contexte de l’opération.|
|`onError`|Entrée Fonction de rapport d’erreurs.|
|`keyPath`|Entrée Valeur de l’attribut de métadonnées [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) pour le CMK référencé par le ECEK donné. Chaîne à caractères larges* se terminant par le caractère Null. Cela vise à identifier un CMK géré par ce fournisseur.|
|`alg`|Entrée Valeur de l' [attribut de](../../t-sql/statements/create-column-encryption-key-transact-sql.md) métadonnées de l’algorithme pour le ECEK donné. Chaîne à caractères larges* se terminant par le caractère Null. Cela vise à identifier l’algorithme de chiffrement utilisé pour chiffrer le ECEK donné.|
|`ecek`|Entrée Pointeur vers le ECEK à déchiffrer.|
|`ecekLen`|Entrée Longueur du ECEK.|
|`cekOut`|Sortie Le fournisseur doit allouer de la mémoire pour le ECEK déchiffré et écrire son adresse sur le pointeur pointé par cekOut. Il doit être possible de libérer ce bloc de mémoire à l’aide de la fonction [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) (Windows) ou Free (Linux/Mac). Si aucune mémoire n’a été allouée en raison d’une erreur ou, le fournisseur doit définir * cekOut sur un pointeur null.|
|`cekLen`|Sortie Le fournisseur écrit dans l’adresse pointée par cekLen la longueur du ECEK déchiffré dans lequel il a écrit * * cekOut.|
|`Return Value`|Retourne une valeur différente de zéro pour indiquer la réussite, ou zéro pour indiquer un échec.|

```
int (*EncryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *cek,unsigned short cekLen, unsigned char **ecekOut, unsigned short *ecekLen);
```
Nom de l’espace réservé pour une fonction de chiffrement clé CEK définie par le fournisseur. Le pilote n’appelle pas cette fonction et n’expose pas ses fonctionnalités par le biais de l’interface ODBC, mais il est fourni pour permettre l’accès par programme à la création de ECEK par les outils de gestion de clés.

|Argument|Description|
|:--|:--|
|`ctx`|Entrée Contexte de l’opération.|
|`onError`|Entrée Fonction de rapport d’erreurs.|
|`keyPath`|Entrée Valeur de l’attribut de métadonnées [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) pour le CMK référencé par le ECEK donné. Chaîne à caractères larges* se terminant par le caractère Null. Cela vise à identifier un CMK géré par ce fournisseur.|
|`alg`|Entrée Valeur de l' [attribut de](../../t-sql/statements/create-column-encryption-key-transact-sql.md) métadonnées de l’algorithme pour le ECEK donné. Chaîne à caractères larges* se terminant par le caractère Null. Cela vise à identifier l’algorithme de chiffrement utilisé pour chiffrer le ECEK donné.|
|`cek`|Entrée Pointeur vers le clé CEK à chiffrer.|
|`cekLen`|Entrée Longueur du clé CEK.|
|`ecekOut`|Sortie Le fournisseur doit allouer de la mémoire pour le clé CEK chiffré et écrire son adresse sur le pointeur pointé par ecekOut. Il doit être possible de libérer ce bloc de mémoire à l’aide de la fonction [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) (Windows) ou Free (Linux/Mac). Si aucune mémoire n’a été allouée en raison d’une erreur ou, le fournisseur doit définir * ecekOut sur un pointeur null.|
|`ecekLen`|Sortie Le fournisseur écrira dans l’adresse pointée par ecekLen la longueur du clé CEK chiffré dans lequel il a écrit * * ecekOut.|
|`Return Value`|Retourne une valeur différente de zéro pour indiquer la réussite, ou zéro pour indiquer un échec.|

```
void (*Free)();
```
Nom de l’espace réservé pour une fonction d’arrêt définie par le fournisseur. Le pilote peut appeler cette fonction à l’issue d’un arrêt normal du processus.

> [!NOTE]
> *Les chaînes à caractères larges sont des caractères de 2 octets (UTF-16) en raison de la façon dont SQL Server les stocke.*


### <a name="error-handling"></a>Gestion des erreurs

Comme des erreurs peuvent se produire pendant le traitement d’un fournisseur, un mécanisme est fourni pour lui permettre de signaler des erreurs au pilote dans des détails plus spécifiques qu’une opération booléenne de réussite/échec. La plupart des fonctions ont une paire de paramètres, **CTX** et **OnError**, qui sont utilisés ensemble à cet effet en plus de la valeur de retour de réussite/échec.

Le paramètre **CTX** identifie le contexte dans lequel une opération de fournisseur se produit.

Le paramètre **OnError** pointe vers une fonction de rapport d’erreurs, avec le prototype suivant:

`typedef void errFunc(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...);`

|Argument|Description|
|:--|:--|
|`ctx`|Entrée Contexte dans lequel signaler l’erreur.|
|`msg`|Entrée Message d’erreur à signaler. Chaîne à caractères larges se terminant par le caractère Null. Pour permettre la présence d’informations paramétrables, cette chaîne peut contenir des séquences d’insertion de mise en forme du formulaire acceptées par la fonction [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) . Les fonctionnalités étendues peuvent être spécifiées par ce paramètre comme décrit ci-dessous.|
|...|Entrée Paramètres variadiques supplémentaires pour ajuster les spécificateurs de format dans le message, le cas échéant.|

Pour signaler qu’une erreur s’est produite, le fournisseur appelle onError, en fournissant le paramètre de contexte passé dans la fonction de fournisseur par le pilote et un message d’erreur avec des paramètres supplémentaires facultatifs à mettre en forme. Le fournisseur peut appeler cette fonction plusieurs fois pour envoyer plusieurs messages d’erreur de façon consécutive dans un appel de fonction fournisseur. Par exemple :

```
    if (!doSomething(...))
    {
        onError(ctx, L"An error occurred in doSomething.");
        onError(ctx, L"Additional error message with more details.");
        return 0;
    }
```


Le `msg` paramètre est généralement une chaîne de caractères larges, mais des extensions supplémentaires sont disponibles:

En utilisant l’une des valeurs prédéfinies spéciales avec la macro IDS_MSG, les messages d’erreur génériques déjà existants et sous une forme localisée dans le pilote peuvent être utilisés. Par exemple, si un fournisseur ne parvient pas à allouer de la mémoire, le message «échec de l' `IDS_S1_001` allocation de mémoire» peut être utilisé:

`onError(ctx, IDS_MSG(IDS_S1_001));`

Pour que l’erreur soit reconnue par le pilote, la fonction du fournisseur doit retourner un échec. Lorsque cette opération est effectuée dans le contexte d’une opération ODBC, les erreurs publiées deviennent accessibles sur la connexion ou le descripteur d’instruction par le biais du`SQLError`mécanisme `SQLGetDiagRec`de Diagnostics ODBC standard (, et `SQLGetDiagField`).


### <a name="context-association"></a>Association de contexte

La `CEKEYSTORECONTEXT` structure, en plus de fournir le contexte pour le rappel d’erreur, peut également être utilisée pour déterminer le contexte ODBC dans lequel une opération de fournisseur est exécutée. Cela permet à un fournisseur d’associer des données à chacun de ces contextes, par exemple pour implémenter une configuration par connexion. À cet effet, la structure contient 3 pointeurs opaques correspondant à l’environnement, la connexion et le contexte d’instruction:

```
typedef struct CEKeystoreContext
{
void *envCtx;
void *dbcCtx;
void *stmtCtx;
} CEKEYSTORECONTEXT;
```

|Champ|Description|
|:--|:--|
|`envCtx`|Contexte d’environnement.|
|`dbcCtx`|Contexte de connexion.|
|`stmtCtx`|Contexte d’instruction.|

Chacun de ces contextes est une valeur opaque qui, même s’il n’est pas identique au handle ODBC correspondant, peut être utilisée comme identificateur unique pour le descripteur: si le handle *X* est associé à la valeur de contexte *Y*, alors aucun autre environnement, connexion ou les descripteurs d’instruction qui existent simultanément en tant que *X* auront une valeur de contexte de *Y*et aucune autre valeur de contexte ne sera associée au handle *X*. Si l’opération du fournisseur en cours d’exécution ne dispose pas d’un contexte de handle particulier, (par exemple, les appels SQLSetConnectAttr pour charger et configurer des fournisseurs, dans lesquels il n’y a aucun descripteur d’instruction), la valeur de contexte correspondante dans la structure est null.


## <a name="example"></a>Exemple

### <a name="keystore-provider"></a>Fournisseur de magasin de clés

Le code suivant est un exemple d’implémentation de fournisseur de magasin de clés minimal.

```
/* Custom Keystore Provider Example

Windows:   compile with cl MyKSP.c /LD /MD /link /out:MyKSP.dll
Linux/Mac: compile with gcc -fshort-wchar -fPIC -o MyKSP.so -shared MyKSP.c

 */

#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#endif

#include <stdlib.h>
#include <sqltypes.h>
#include "msodbcsql.h"
#include <sql.h>
#include <sqlext.h>

int __stdcall KeystoreInit(CEKEYSTORECONTEXT *ctx, errFunc *onError) {
    printf("KSP Init() function called\n");
    return 1;
}

static unsigned char *g_encryptKey;
static unsigned int g_encryptKeyLen;

int __stdcall KeystoreWrite(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len) {
    printf("KSP Write() function called (%d bytes)\n", len);
    if (len) {
        if (g_encryptKey)
            free(g_encryptKey);
        g_encryptKey = malloc(len);
        if (!g_encryptKey) {
            onError(ctx, L"Memory Allocation Error");
            return 0;
        }
        memcpy(g_encryptKey, data, len);
        g_encryptKeyLen = len;
    }
    return 1;
}

// Very simple "encryption" scheme - rotating XOR with the key
int __stdcall KeystoreDecrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg,
    unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen) {
    unsigned int i;
    printf("KSP Decrypt() function called (keypath=%S alg=%S ecekLen=%u)\n", keyPath, alg, ecekLen);
    if (wcscmp(keyPath, L"TheOneAndOnlyKey")) {
        onError(ctx, L"Invalid key path");
        return 0;
    }
    if (wcscmp(alg, L"none")) {
        onError(ctx, L"Invalid algorithm");
        return 0;
    }
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
#ifndef _WIN32
    *cekOut = malloc(ecekLen);
#else
    *cekOut = LocalAlloc(LMEM_FIXED, ecekLen);
#endif
    if (!*cekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *cekLen = ecekLen;
    for (i = 0; i < ecekLen; i++)
        (*cekOut)[i] = ecek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

// Note that in the provider interface, this function would be referenced via the CEKEYSTOREPROVIDER
// structure. However, that does not preclude keystore providers from exporting their own functions,
// as illustrated by this example where the encryption is performed via a separate function (with a
// different prototype than the one in the KSP interface.)
#ifdef _WIN32
__declspec(dllexport)
#endif
int KeystoreEncrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError,
    unsigned char *cek, unsigned short cekLen,
    unsigned char **ecekOut, unsigned short *ecekLen) {
    unsigned int i;
    printf("KSP Encrypt() function called (cekLen=%u)\n", cekLen);
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
    *ecekOut = malloc(cekLen);
    if (!*ecekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *ecekLen = cekLen;
    for (i = 0; i < cekLen; i++)
        (*ecekOut)[i] = cek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

CEKEYSTOREPROVIDER MyCustomKSPName_desc = {
    L"MyCustomKSPName",
    KeystoreInit,
    0,
    KeystoreWrite,
    KeystoreDecrypt,
    0
};

#ifdef _WIN32
__declspec(dllexport)
#endif
CEKEYSTOREPROVIDER *CEKeystoreProvider[] = {
    &MyCustomKSPName_desc,
    0
};
```

### <a name="odbc-application"></a>Application ODBC

Le code suivant est une application de démonstration qui utilise le fournisseur de magasin de clés ci-dessus. Lors de son exécution, assurez-vous que la bibliothèque du fournisseur se trouve dans le même répertoire que le fichier binaire de l’application, et que la chaîne de connexion `ColumnEncryption=Enabled` spécifie (ou spécifie un nom de source de fichiers qui contient) le paramètre.

```
/*
 Example application for demonstration of custom keystore provider usage

Windows:   compile with cl /MD kspapp.c /link odbc32.lib
Linux/Mac: compile with gcc -o kspapp -fshort-wchar kspapp.c -lodbc -ldl
 
 usage: kspapp connstr

 */

#define KSPNAME L"MyCustomKSPName"
#define PROV_ENCRYPT_KEY "JHKCWYT06N3RG98J0MBLG4E3"

#include <stdio.h>
#include <stdlib.h>
#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#include <dlfcn.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include "msodbcsql.h"

/* Convenience functions */

int checkRC(SQLRETURN rc, char *msg, int ret, SQLHANDLE h, SQLSMALLINT ht) {
    if (rc == SQL_ERROR) {
        fprintf(stderr, "Error occurred upon %s\n", msg);
        if (h) {
            SQLSMALLINT i = 0;
            SQLSMALLINT outlen = 0;
            char errmsg[1024];
            while ((rc = SQLGetDiagField(
                ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
                || rc == SQL_SUCCESS_WITH_INFO) {
                fprintf(stderr, "Err#%d: %s\n", i, errmsg);
            }
        }
        if (ret)
            exit(ret);
        return 0;
    }
    else if (rc == SQL_SUCCESS_WITH_INFO && h) {
        SQLSMALLINT i = 0;
        SQLSMALLINT outlen = 0;
        char errmsg[1024];
        printf("Success with info for %s:\n", msg);
        while ((rc = SQLGetDiagField(
            ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
            || rc == SQL_SUCCESS_WITH_INFO) {
            fprintf(stderr, "Msg#%d: %s\n", i, errmsg);
        }
    }
    return 1;
}

void postKspError(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...) {
    if (msg > (wchar_t*)65535)
        wprintf(L"Provider emitted message: %s\n", msg);
    else
        wprintf(L"Provider emitted message ID %d\n", msg);
}

int main(int argc, char **argv) {
    char sqlbuf[1024];
    SQLHENV env;
    SQLHDBC dbc;
    SQLHSTMT stmt;
    SQLRETURN rc;
    unsigned char CEK[32];
    unsigned char *ECEK;
    unsigned short ECEKlen;
#ifdef _WIN32
    HMODULE hProvLib;
#else
    void *hProvLib;
#endif
    CEKEYSTORECONTEXT ctx = {0};
    CEKEYSTOREPROVIDER **ppKsp, *pKsp;
    int(__stdcall *pEncryptCEK)(CEKEYSTORECONTEXT *, errFunc *, unsigned char *, unsigned short, unsigned char **, unsigned short *);
    int i;
    if (argc < 2) {
        fprintf(stderr, "usage: kspapp connstr\n");
        return 1;
    }

    /* Load the provider library */
#ifdef _WIN32
    if (!(hProvLib = LoadLibrary("MyKSP.dll"))) {
#else
    if (!(hProvLib = dlopen("./MyKSP.so", RTLD_NOW))) {
#endif
        fprintf(stderr, "Error loading KSP library\n");
        return 2;
    }
#ifdef _WIN32
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)GetProcAddress(hProvLib, "CEKeystoreProvider"))) {
#else
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)dlsym(hProvLib, "CEKeystoreProvider"))) {
#endif
        fprintf(stderr, "The export CEKeystoreProvider was not found in the KSP library\n");
        return 3;
    }
    while (pKsp = *ppKsp++) {
        if (!memcmp(KSPNAME, pKsp->Name, sizeof(KSPNAME)))
            goto FoundProv;
    }
    fprintf(stderr, "Could not find provider in the library\n");
    return 4;
FoundProv:
    if (pKsp->Init && !pKsp->Init(&ctx, postKspError)) {
        fprintf(stderr, "Could not initialize provider\n");
        return 5;
    }
#ifdef _WIN32
    if (!(pEncryptCEK = (LPVOID)GetProcAddress(hProvLib, "KeystoreEncrypt"))) {
#else
    if (!(pEncryptCEK = dlsym(hProvLib, "KeystoreEncrypt"))) {
#endif
        fprintf(stderr, "The export KeystoreEncrypt was not found in the KSP library\n");
        return 6;
    }
    if (!pKsp->Write) {
        fprintf(stderr, "Provider does not support configuration\n");
        return 7;
    }

    /* Configure the provider with the key */
    if (!pKsp->Write(&ctx, postKspError, PROV_ENCRYPT_KEY, strlen(PROV_ENCRYPT_KEY))) {
        fprintf(stderr, "Error writing to KSP\n");
        return 8;
    }

    /* Generate a CEK and encrypt it with the provider */
    srand(time(0) ^ getpid());
    for (i = 0; i < sizeof(CEK); i++)
        CEK[i] = rand();

    if (!pEncryptCEK(&ctx, postKspError, CEK, sizeof(CEK), &ECEK, &ECEKlen)) {
        fprintf(stderr, "Error encrypting CEK\n");
        return 9;
    }

    /* Connect to Server */
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &env);
    checkRC(rc, "allocating environment handle", 2, 0, 0);
    rc = SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0);
    checkRC(rc, "setting ODBC version to 3.0", 3, env, SQL_HANDLE_ENV);
    rc = SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc);
    checkRC(rc, "allocating connection handle", 4, env, SQL_HANDLE_ENV);
    rc = SQLDriverConnect(dbc, 0, argv[1], strlen(argv[1]), NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
    checkRC(rc, "connecting to data source", 5, dbc, SQL_HANDLE_DBC);
    rc = SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt);
    checkRC(rc, "allocating statement handle", 6, dbc, SQL_HANDLE_DBC);

    /* Create a CMK definition on the server */
    {
        static char cmkSql[] = "CREATE COLUMN MASTER KEY CustomCMK WITH ("
            "KEY_STORE_PROVIDER_NAME = 'MyCustomKSPName',"
            "KEY_PATH = 'TheOneAndOnlyKey')";
        printf("Create CMK: %s\n", cmkSql);
        SQLExecDirect(stmt, cmkSql, SQL_NTS);
    }

    /* Create a CEK definition on the server */
    {
        const char cekSqlBefore[] = "CREATE COLUMN ENCRYPTION KEY CustomCEK WITH VALUES ("
            "COLUMN_MASTER_KEY = CustomCMK,"
            "ALGORITHM = 'none',"
            "ENCRYPTED_VALUE = 0x";
        char *cekSql = malloc(sizeof(cekSqlBefore) + 2 * ECEKlen + 2); /* 1 for ')', 1 for null terminator */
        strcpy(cekSql, cekSqlBefore);
        for (i = 0; i < ECEKlen; i++)
            sprintf(cekSql + sizeof(cekSqlBefore) - 1 + 2 * i, "%02x", ECEK[i]);
        strcat(cekSql, ")");
        printf("Create CEK: %s\n", cekSql);
        SQLExecDirect(stmt, cekSql, SQL_NTS);
        free(cekSql);
#ifdef _WIN32
        LocalFree(ECEK);
#else
        free(ECEK);
#endif
    }

#ifdef _WIN32
    FreeLibrary(hProvLib);
#else
    dlclose(hProvLib);
#endif

    /* Create a table with encrypted columns */
    {
        static char *tableSql = "CREATE TABLE CustomKSPTestTable ("
            "c1 int,"
            "c2 varchar(255) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = CustomCEK, ENCRYPTION_TYPE = DETERMINISTIC, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'))";
        printf("Create table: %s\n", tableSql);
        SQLExecDirect(stmt, tableSql, SQL_NTS);
    }

    /* Load provider into the ODBC Driver and configure it */
    {
        unsigned char ksd[sizeof(CEKEYSTOREDATA) + sizeof(PROV_ENCRYPT_KEY) - 1];
        CEKEYSTOREDATA *pKsd = (CEKEYSTOREDATA*)ksd;
        pKsd->name = L"MyCustomKSPName";
        pKsd->dataSize = sizeof(PROV_ENCRYPT_KEY) - 1;
        memcpy(pKsd->data, PROV_ENCRYPT_KEY, sizeof(PROV_ENCRYPT_KEY) - 1);
#ifdef _WIN32
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "MyKSP.dll", SQL_NTS);
#else
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "./MyKSP.so", SQL_NTS);
#endif
        checkRC(rc, "Loading KSP into ODBC Driver", 7, dbc, SQL_HANDLE_DBC);
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREDATA, (SQLPOINTER)pKsd, SQL_IS_POINTER);
        checkRC(rc, "Configuring the KSP", 7, dbc, SQL_HANDLE_DBC);
    }

    /* Insert some data */
    {
        int c1;
        char c2[256];
        rc = SQLBindParameter(stmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 0, 0, &c1, 0, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        rc = SQLBindParameter(stmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_VARCHAR, 255, 0, c2, 255, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        for (i = 0; i < 10; i++) {
            c1 = i * 10 + i + 1;
            sprintf(c2, "Sample data %d for column 2", i);
            rc = SQLExecDirect(stmt, "INSERT INTO CustomKSPTestTable (c1, c2) values (?, ?)", SQL_NTS);
            checkRC(rc, "Inserting rows query", 10, stmt, SQL_HANDLE_STMT);
        }
        printf("(Encrypted) data has been inserted into the [CustomKSPTestTable]. You may inspect the data now.\n"
            "Press Enter to continue...\n");
        getchar();
    }

    /* Retrieve the data */
    {
        int c1;
        char c2[256];
        rc = SQLBindCol(stmt, 1, SQL_C_LONG, &c1, 0, 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLBindCol(stmt, 2, SQL_C_CHAR, c2, sizeof(c2), 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLExecDirect(stmt, "SELECT c1, c2 FROM CustomKSPTestTable", SQL_NTS);
        checkRC(rc, "Retrieving rows query", 12, stmt, SQL_HANDLE_STMT);
        while (SQL_SUCCESS == (rc = SQLFetch(stmt)))
            printf("Retrieved data: c1=%d c2=%s\n", c1, c2);
        SQLFreeStmt(stmt, SQL_CLOSE);
        printf("Press Enter to clean up and exit...\n");
        getchar();
    }

    /* Clean up */
    {
        SQLExecDirect(stmt, "DROP TABLE CustomKSPTestTable", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN ENCRYPTION KEY CustomCEK", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN MASTER KEY CustomCMK", SQL_NTS);
        printf("Removed table, CEK, and CMK\n");
    }
    SQLDisconnect(dbc);
    SQLFreeHandle(SQL_HANDLE_DBC, dbc);
    SQLFreeHandle(SQL_HANDLE_ENV, env);
    return 0;
}

```

## <a name="see-also"></a>Voir aussi

[Utilisation d’Always Encrypted avec ODBC Driver](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
