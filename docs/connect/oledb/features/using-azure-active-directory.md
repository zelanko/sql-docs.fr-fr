---
title: À l’aide d’Azure Active Directory | Documentation de Microsoft pour SQL Server
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: 44f92e782a497005ea47847301279e4341722d36
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744825"
---
# <a name="using-azure-active-directory"></a>Utilisation d’Azure Active Directory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>Fonction

Avec la version 18.2.1, Microsoft OLE DB Driver pour SQL Server autorise les applications OLE DB pour se connecter à une instance de base de données SQL Azure à l’aide d’une identité fédérée. Les méthodes d’authentification sont les suivantes :
- ID de connexion Azure Active Directory et le mot de passe
- Jeton d’accès Azure Active Directory
- Authentification intégrée à Azure Active Directory
- ID de connexion SQL et le mot de passe

> [!NOTE]  
> Lorsque vous utilisez les options d’Azure Active Directory suivantes avec le pilote OLE DB, assurez-vous que le [Active Directory Authentication Library pour SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) a été installé :
> - ID de connexion Azure Active Directory et le mot de passe
> - Authentification intégrée à Azure Active Directory
>
> La bibliothèque ADAL n’est pas requise pour les autres méthodes d’authentification ou les opérations de OLE DB.

> [!NOTE]
> À l’aide des modes d’authentification ci-dessous avec `DataTypeCompatibility` (ou sa propriété correspondante) la valeur `80` est **pas** pris en charge :
> - Authentification Azure Active Directory à l’aide d’un ID de connexion et mot de passe
> - Authentification Azure Active Directory à l’aide du jeton d’accès
> - Authentification intégrée à Azure Active Directory

## <a name="connection-string-keywords-and-properties"></a>Propriétés et les mots clés de chaîne de connexion
Les mots clés de chaîne de connexion suivantes ont été introduites pour prendre en charge l’authentification Azure Active Directory :

|Mot clé de chaîne de connexion|Propriété de connexion|Description|
|---               |---                |---        |
|Jeton d'accès|SSPROP_AUTH_ACCESS_TOKEN|Spécifie un jeton d’accès pour s’authentifier auprès d’Azure Active Directory. |
|Authentification|SSPROP_AUTH_MODE|Spécifie la méthode d’authentification à utiliser.|

Pour plus d’informations sur les nouveaux mots clés/propriétés, consultez les pages suivantes :
- [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Propriétés d’initialisation et d’autorisation](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>Chiffrement et validation des certificats
Cette section traite des modifications apportées dans le chiffrement et le comportement de validation de certificat. Ces modifications sont **uniquement** efficace lorsque vous utilisez les nouveau jeton d’accès ou de l’authentification de connexion mots clés de chaîne (ou leurs propriétés correspondantes).

### <a name="encryption"></a>Chiffrement
Pour améliorer la sécurité, lorsque les nouvelle connexion propriétés/mots clés sont utilisés, le pilote remplace la valeur de chiffrement par défaut en lui affectant `yes`. Substitution se produit au moment de l’initialisation de données source objet. Si le chiffrement est défini avant l’initialisation par tout moyen, la valeur est respectée et ne pas remplacée.

> [!NOTE]   
> Dans les applications ADO et dans les applications qui obtiennent la `IDBInitialize` par le biais de l’interface `IDataInitialize::GetDataSource`, le composant principal qui implémente l’interface explicitement définit le chiffrement à sa valeur par défaut de `no`. Par conséquent, les nouvelles propriétés/mots clés d’authentification respectent ce paramètre et la valeur de chiffrement **n’est pas** substitution. Par conséquent, il est **recommandé** que ces applications explicitement définissent `Use Encryption for Data=true` pour remplacer la valeur par défaut.

### <a name="certificate-validation"></a>Validation du certificat
Pour améliorer la sécurité, les nouvelles propriétés/mots clés de connexion respectent la `TrustServerCertificate` paramètre (et sa connexion chaîne mots clés/propriétés correspondantes) **indépendamment du paramètre de chiffrement client**. Par conséquent, le certificat de serveur est validé par défaut.

> [!NOTE]   
> Validation de certificat peut également être contrôlée via la `Value` champ la `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2` entrée de Registre. Les valeurs valides sont `0` ou `1`. Le pilote OLE DB choisit l’option la plus sécurisée entre le Registre et les paramètres de propriété/mot clé de connexion. Autrement dit, le pilote validera le certificat de serveur tant qu’au moins un des paramètres de Registre/connexion active la validation de certificat serveur.

## <a name="gui-additions"></a>Ajouts de l’interface graphique utilisateur
L’interface utilisateur graphique de pilote a été amélioré pour permettre l’authentification Azure Active Directory. Pour plus d'informations, consultez :
- [Boîte de dialogue de connexion à SQL Server](../help-topics/sql-server-login-dialog.md)
- [Configuration de liaison (UDL) de données universel](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>Exemples de chaîne de connexion
Cette section présente des exemples de connexion nouvelle et existante mots clés de chaîne à utiliser avec `IDataInitialize::GetDataSource` et `DBPROP_INIT_PROVIDERSTRING` propriété.

### <a name="sql-authentication"></a>Authentification SQL
- Utilisation de `IDataInitialize::GetDataSource`:
    - Nouveau :
        > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Authentication=SqlPassword**;User ID=[username];Password=[password];Use Encryption for Data=true
    - Déconseillé :
        > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];User ID=[username];Password=[password];Use Encryption for Data=true
- Utilisation de `DBPROP_INIT_PROVIDERSTRING`:
    - Nouveau :
        > Server=[server];Database=[database];**Authentication=SqlPassword**;UID=[username];PWD=[password];Encrypt=yes
    - Déconseillé :
        > Server=[server];Database=[database];UID=[username];PWD=[password];Encrypt=yes

### <a name="integrated-windows-authentication-using-security-support-provider-interface--sspi"></a>Authentification Windows intégrée à l’aide de la prise en charge Interface SSPI (Security Provider)

- Utilisation de `IDataInitialize::GetDataSource`:
    - Nouveau :
        > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Authentication=ActiveDirectoryIntegrated**;Use Encryption for Data=true
    - Déconseillé :
        > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Integrated Security=SSPI**;Use Encryption for Data=true
- Utilisation de `DBPROP_INIT_PROVIDERSTRING`:
    - Nouveau :
        > Server=[server];Database=[database];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes
    - Déconseillé :
        > Server=[server];Database=[database];**Trusted_Connection=yes**;Encrypt=yes

### <a name="aad-username-and-password-authentication-using-adal"></a>Nom d’utilisateur et mot de passe l’authentification AAD à l’aide de la bibliothèque ADAL

- Utilisation de `IDataInitialize::GetDataSource`:
    > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Authentication=ActiveDirectoryPassword**;User ID=[username];Password=[password];Use Encryption for Data=true
- Utilisation de `DBPROP_INIT_PROVIDERSTRING`:
    > Server=[server];Database=[database];**Authentication=ActiveDirectoryPassword**;UID=[username];PWD=[password];Encrypt=yes

### <a name="integrated-azure-active-directory-authentication-using-adal"></a>Authentification Azure Active Directory intégrée à l’aide de la bibliothèque ADAL

- Utilisation de `IDataInitialize::GetDataSource`:
    > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Authentication=ActiveDirectoryIntegrated**;Use Encryption for Data=true
- Utilisation de `DBPROP_INIT_PROVIDERSTRING`:
    > Server=[server];Database=[database];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes

### <a name="azure-active-directory-authentication-using-an-access-token"></a>Authentification Azure Active Directory à l’aide d’un jeton d’accès

- Utilisation de `IDataInitialize::GetDataSource`:
    > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Access Token=[access token]**;Use Encryption for Data=true
- Utilisation de `DBPROP_INIT_PROVIDERSTRING`:
    > Jeton d’accès en fournissant via `DBPROP_INIT_PROVIDERSTRING` n’est pas pris en charge

## <a name="code-samples"></a>Exemples de code

Les exemples suivants montrent le code requis pour se connecter à Azure Active Directory avec les mots clés de connexion. 

### <a name="access-token"></a>Jeton d'accès
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    wchar_t accessToken[] = L"eyJ0eXAiOi...";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Access Token=" + accessToken + L";Use Encryption for Data=true;";
    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```
### <a name="active-directory-integrated"></a>Active Directory intégré
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Authentication=ActiveDirectoryIntegrated;Use Encryption for Data=true;";

    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr)) 
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```

## <a name="next-steps"></a>Étapes suivantes
- [Autoriser l’accès aux applications web de Azure Active Directory à l’aide de flux d’octroi de code OAuth 2.0](https://go.microsoft.com/fwlink/?linkid=2072672).

- En savoir plus sur l’[authentification Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2073783) sur SQL Server.

- Configurer des connexions de pilote à l’aide de [mots clés de chaîne de connexion](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md) le pilote OLE DB prend en charge.
