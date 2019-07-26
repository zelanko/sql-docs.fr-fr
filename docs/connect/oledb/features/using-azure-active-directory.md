---
title: Utilisation de Azure Active Directory | Microsoft Docs pour SQL Server
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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68213552"
---
# <a name="using-azure-active-directory"></a>Utilisation d’Azure Active Directory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>Fonction

À partir de la version 18.2.1, le pilote Microsoft OLE DB pour SQL Server permet aux applications OLE DB de se connecter à une instance de Azure SQL Database à l’aide d’une identité fédérée. Les nouvelles méthodes d’authentification sont les suivantes:
- ID de connexion et mot de passe Azure Active Directory
- Jeton d’accès Azure Active Directory
- Authentification intégrée à Azure Active Directory
- ID de connexion SQL et mot de passe

> [!NOTE]  
> Lorsque vous utilisez les options de Azure Active Directory suivantes avec le pilote OLE DB, assurez-vous que le [bibliothèque d’Authentification Active Directory pour SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) a été installé:
> - ID de connexion et mot de passe Azure Active Directory
> - Authentification intégrée à Azure Active Directory
>
> ADAL n’est pas requis pour les autres méthodes d’authentification ou les opérations de OLE DB.

> [!NOTE]
> L’utilisation des modes d’authentification `DataTypeCompatibility` suivants avec (ou la propriété correspondante) `80` définie sur n’est **pas** prise en charge:
> - Authentification Azure Active Directory à l’aide de l’ID de connexion et du mot de passe
> - Authentification Azure Active Directory à l’aide d’un jeton d’accès
> - Authentification intégrée à Azure Active Directory

## <a name="connection-string-keywords-and-properties"></a>Mots clés de chaîne de connexion et propriétés
Les mots clés de chaîne de connexion suivants ont été introduits pour prendre en charge l’authentification Azure Active Directory:

|Mot clé de chaîne de connexion|Propriété de connexion|Description|
|---               |---                |---        |
|Jeton d'accès|SSPROP_AUTH_ACCESS_TOKEN|Spécifie un jeton d’accès pour s’authentifier auprès de Azure Active Directory. |
|Authentification|SSPROP_AUTH_MODE|Spécifie la méthode d’authentification à utiliser.|

Pour plus d’informations sur les nouveaux mots clés/propriétés, consultez les pages suivantes:
- [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Propriétés d’initialisation et d’autorisation](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>Chiffrement et validation des certificats
Cette section traite des modifications apportées au chiffrement et au comportement de validation des certificats. Ces modifications sont effectives **uniquement** lors de l’utilisation des mots clés de chaîne de connexion de jeton d’accès ou d’authentification (ou leurs propriétés correspondantes).

### <a name="encryption"></a>Chiffrement
Pour améliorer la sécurité, lorsque les nouvelles propriétés/Mots clés de connexion sont utilisés, le pilote remplace la valeur de chiffrement par défaut `yes`en lui affectant la valeur. La substitution se produit au moment de l’initialisation de l’objet source de données. Si le chiffrement est défini avant l’initialisation par quelque moyen que ce soit, la valeur est respectée et n’est pas remplacée.

> [!NOTE]   
> Dans les applications ADO et dans les applications qui `IDBInitialize` obtiennent l' `IDataInitialize::GetDataSource`interface via, le composant principal qui implémente l’interface définit explicitement le chiffrement `no`sur sa valeur par défaut. Par conséquent, les nouveaux mots clés/propriétés d’authentification respectent ce paramètre et la valeur de chiffrement **n’est pas** remplacée. Par conséquent, il est **recommandé** que ces applications soient `Use Encryption for Data=true` explicitement définies pour remplacer la valeur par défaut.

### <a name="certificate-validation"></a>Validation du certificat
Pour améliorer la sécurité, les nouveaux mots clés/propriétés de `TrustServerCertificate` connexion respectent le paramètre (et les mots clés/propriétés **de la chaîne de connexion correspondante) indépendamment du paramètre de chiffrement du client**. Par conséquent, le certificat de serveur est validé par défaut.

> [!NOTE]   
> La validation de certificat peut également être contrôlée `Value` par le biais `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2` du champ de l’entrée de registre. Les valeurs valides sont `0` ou `1`. Le pilote OLE DB choisit l’option la plus sécurisée entre le registre et les paramètres de mot de passe/propriété de connexion. Autrement dit, le pilote validera le certificat de serveur tant qu’au moins l’un des paramètres du registre/de la connexion active la validation du certificat du serveur.

## <a name="gui-additions"></a>Ajouts de GUI
L’interface utilisateur graphique du pilote a été améliorée pour permettre l’authentification Azure Active Directory. Pour plus d'informations, consultez :
- [Boîte de dialogue de connexion à SQL Server](../help-topics/sql-server-login-dialog.md)
- [Configuration UDL (Universal Data Link)](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>Exemples de chaîne de connexion
Cette section présente des exemples de mots clés de chaîne de connexion nouveaux et existants `IDataInitialize::GetDataSource` à `DBPROP_INIT_PROVIDERSTRING` utiliser avec la propriété et.

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

### <a name="integrated-windows-authentication-using-security-support-provider-interface--sspi"></a>Authentification Windows intégrée à l’aide de SSPI (Security Support Provider Interface)

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

### <a name="aad-username-and-password-authentication-using-adal"></a>Authentification du nom d’utilisateur et du mot de passe AAD à l’aide de ADAL

- Utilisation de `IDataInitialize::GetDataSource`:
    > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Authentication=ActiveDirectoryPassword**;User ID=[username];Password=[password];Use Encryption for Data=true
- Utilisation de `DBPROP_INIT_PROVIDERSTRING`:
    > Server=[server];Database=[database];**Authentication=ActiveDirectoryPassword**;UID=[username];PWD=[password];Encrypt=yes

### <a name="integrated-azure-active-directory-authentication-using-adal"></a>Authentification Azure Active Directory intégrée à l’aide de ADAL

- Utilisation de `IDataInitialize::GetDataSource`:
    > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Authentication=ActiveDirectoryIntegrated**;Use Encryption for Data=true
- Utilisation de `DBPROP_INIT_PROVIDERSTRING`:
    > Server=[server];Database=[database];**Authentication=ActiveDirectoryIntegrated**;Encrypt=yes

### <a name="azure-active-directory-authentication-using-an-access-token"></a>Azure Active Directory de l’authentification à l’aide d’un jeton d’accès

- Utilisation de `IDataInitialize::GetDataSource`:
    > Provider=MSOLEDBSQL;Data Source=[server];Initial Catalog=[database];**Access Token=[access token]** ;Use Encryption for Data=true
- Utilisation de `DBPROP_INIT_PROVIDERSTRING`:
    > Le fait de fournir `DBPROP_INIT_PROVIDERSTRING` un jeton d’accès n’est pas pris en charge

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
- [Autorisez l’accès aux applications web Azure Active Directory à l’aide du workflow d’octroi de code OAuth 2,0](https://go.microsoft.com/fwlink/?linkid=2072672).

- En savoir plus sur l’[authentification Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2073783) sur SQL Server.

- Configurer des connexions de pilote à l’aide de [Mots clés de chaîne de connexion](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md) pris en charge par le pilote OLE DB.
