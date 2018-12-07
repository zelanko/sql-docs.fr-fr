---
title: CREATE COLUMN MASTER KEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SQL13.SWB.NEWCOLUMNMASTERKEYDEF.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEYDEF.GENERAL.F1
- CREATE COLUMN MASTER KEY
- COLUMN MASTER KEY
- CREATE_COLUMN_MASTER_KEY_TSQL
- COLUMN_MASTER_KEY_TSQL
- SQL13.SWB.NEWCOLUMNMASTERKEY.GENERAL.F1
- SQL13.SWB.COLUMNMASTERKEY.GENERAL.F1
dev_langs:
- TSQL
helpviewer_keywords:
- column master key definition
- column master key, create
- CREATE COLUMN MASTER KEY statement
- Always Encrypted, create column master key
ms.assetid: f8926b95-e146-4e3f-b56b-add0c0d0a30e
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 81fd7b18058430b3132471f67a8b94e4444873e7
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52393042"
---
# <a name="create-column-master-key-transact-sql"></a>CREATE COLUMN MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Crée un objet de métadonnées de clé principale de colonne dans une base de données. Une entrée de métadonnées de clé principale de colonne qui représente une clé, stockée dans un magasin de clés externe, qui sert à protéger (chiffrer) les clés de chiffrement de colonne quand vous utilisez la fonctionnalité [Always Encrypted &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Le fait d’avoir plusieurs clés principales de colonne autorise la rotation de clé, c’est-à-dire le changement périodique de la clé afin d’améliorer la sécurité. Vous pouvez créer une clé principale de colonne dans un magasin de clés et son objet de métadonnées correspondant dans la base de données à l’aide de l’Explorateur d’objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou PowerShell. Pour plus d’informations, consultez [Vue d’ensemble de la gestion des clés pour Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
 

> [!IMPORTANT]
> La création de clés prenant en charge les enclaves (avec ENCLAVE_COMPUTATIONS) nécessite [Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

## <a name="syntax"></a>Syntaxe  

```  
CREATE COLUMN MASTER KEY key_name   
    WITH (  
        KEY_STORE_PROVIDER_NAME = 'key_store_provider_name',  
        KEY_PATH = 'key_path'   
        [,ENCLAVE_COMPUTATIONS (SIGNATURE = signature)]
         )   
[;]  
```  
  
## <a name="arguments"></a>Arguments  
 *key_name*  
 Nom sous lequel la clé principale de colonne sera connue dans la base de données.  
  
 *key_store_provider_name*  
 Spécifie le nom d’un fournisseur de magasin de clés principales de colonne, qui est un composant logiciel côté client qui encapsule un magasin de clés contenant la clé principale de colonne. Un pilote client compatible avec Always Encrypted utilise un nom de fournisseur de magasin de clés pour rechercher un fournisseur de magasin de clés dans le Registre de fournisseurs de magasin de clés du pilote. Le pilote utilise le fournisseur pour déchiffrer les clés de chiffrement de colonne, protégées par une clé principale de colonne, stockée dans le magasin de clés sous-jacent. Une valeur en texte brut de la clé de chiffrement de colonne est ensuite utilisée pour chiffrer les paramètres de requête, correspondant aux colonnes de base de données chiffrées, ou pour déchiffrer les résultats de requête à partir des colonnes chiffrées.  
  
 Les bibliothèques de pilotes clients compatibles avec Always Encrypted incluent des fournisseurs de magasin de clés pour les magasins de clés les plus populaires.   
  
Un ensemble de fournisseurs disponibles varie en fonction du type et de la version du pilote client. Pour plus d’informations sur des pilotes spécifiques, consultez la documentation Always Encrypted :

[Développer à l’aide d’Always Encrypted avec le Fournisseur de données .NET Framework pour SQL Server](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)


Les tableaux ci-dessous capturent les noms des fournisseurs de système :  
  
|Nom du fournisseur de magasin de clés|Magasin de clés sous-jacent|  
    |-----------------------------|--------------------------|
    |'MSSQL_CERTIFICATE_STORE'|Magasin de certificats Windows| 
    |'MSSQL_CSP_PROVIDER'|Un magasin, tel qu’un module de sécurité matériel (HSM), qui prend en charge Microsoft CryptoAPI.|
    |'MSSQL_CNG_STORE'|Un magasin, tel qu’un module de sécurité matériel (HSM), qui prend en charge l’API CNG (Cryptography Next Generation).|  
    |'Azure_Key_Vault'|Voir [Prise en main du coffre de clés Azure](https://azure.microsoft.com/documentation/articles/key-vault-get-started/).|  
  

 Vous pouvez implémenter un fournisseur de magasins de clés personnalisé pour stocker les clés principales de colonne dans un magasin pour lequel il n’existe aucun fournisseur de magasin de clés intégré dans votre pilote client compatible avec Always Encrypted.  Notez que les noms des fournisseurs de magasins de clés personnalisés ne peuvent pas commencer par 'MSSQL_', qui est un préfixe réservé pour les fournisseurs de magasins de clés [!INCLUDE[msCoName](../../includes/msconame-md.md)]. 

  
 key_path  
 Chemin de la clé dans le magasin de clés principales de colonne. Le chemin de clé doit être valide dans le contexte de chaque application cliente qui est censée chiffrer ou déchiffrer des données stockées dans une colonne protégée (indirectement) par la clé principale de colonne référencée, et l’application cliente doit être autorisée à accéder à la clé. Le format du chemin de clé est propre au fournisseur de magasin de clés. La liste suivante décrit le format des chemins de clés pour des fournisseurs de magasins de clés de système Microsoft particuliers.  
  
-   **Nom du fournisseur :** MSSQL_CERTIFICATE_STORE  
  
     **Format du chemin de clé :** *nom_magasin_certificats*/*emplacement_magasin_certificats*/*empreinte_certificat*  
  
     Où :  
  
     *emplacement_magasin_certificats*  
     Emplacement du magasin de certificats, qui doit être Current User ou Local Machine. Pour plus d’informations, consultez [Local Machine and Current User Certificate Stores](https://msdn.microsoft.com/library/windows/hardware/ff548653.aspx).  
  
     *nom_magasin_certificats*  
     Nom du magasin de certificats, par exemple 'My'.  
  
     *empreinte_certificat*  
     Empreinte du certificat.  
  
     **Exemples :**  
  
    ```  
    N'CurrentUser/My/BBF037EC4A133ADCA89FFAEC16CA5BFA8878FB94'  
  
    N'LocalMachine/My/CA5BFA8878FB94BBF037EC4A133ADCA89FFAEC16'  
    ```  
  
-   **Nom du fournisseur :** MSSQL_CSP_PROVIDER  
  
     **Format du chemin de clé :** *nom_fournisseur*/*identificateur_clé*  
  
     Où :  
  
     *ProviderName*  
     Nom d’un fournisseur de service de chiffrement, qui implémente CAPI, pour le magasin de clés principales de colonne. Si vous utilisez un module HSM comme magasin de clés, il doit s’agir du nom du fournisseur de service de chiffrement fourni par le fournisseur de votre module HSM. Le fournisseur doit être installé sur un ordinateur client.  
  
     *identificateur_clé*  
     Identificateur de la clé, utilisé comme clé principale de colonne, dans le magasin de clés.  
  
     **Exemples :**  
  
    ```  
    N'My HSM CSP Provider/AlwaysEncryptedKey1'  
    ```  
  
-   **Nom du fournisseur :** MSSQL_CNG_STORE  
  
     **Format du chemin de clé :** *nom_fournisseur*/*identificateur_clé*  
  
     Où :  
  
     *ProviderName*  
     Nom du fournisseur de stockage de clés (KSP), qui implémente l’API CNG (Cryptography Next Generation), pour le magasin de clés principales de colonne. Si vous utilisez un module HSM comme magasin de clés, il doit s’agir du nom du fournisseur de stockage de clés fourni par le fournisseur de votre module HSM. Le fournisseur doit être installé sur un ordinateur client.  
  
     *identificateur_clé*  
     Identificateur de la clé, utilisé comme clé principale de colonne, dans le magasin de clés.  
  
     **Exemples :**  
  
    ```  
    N'My HSM CNG Provider/AlwaysEncryptedKey1'  
    ```  

-   **Nom du fournisseur :** AZURE_KEY_STORE  
  
     **Format du chemin de clé :** *URL_clé*  
  
     Où :  
  
     *URL_clé*  
     URL de la clé dans Azure Key Vault.

ENCLAVE_COMPUTATIONS  
Spécifie que la clé principale de colonne prend en charge les enclaves, ce qui signifie que toutes les clés de chiffrement de colonne chiffrées avec cette clé principale de colonne peuvent être partagées avec une enclave sécurisée côté serveur et utilisées pour effectuer des calculs dans l’enclave. Pour plus d’informations, consultez [Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

 *signature*  
Littéral binaire qui est le résultat de la signature numérique du *chemin de clé* et du paramètre ENCLAVE_COMPUTATIONS avec la clé principale de colonne (la signature reflète si ENCLAVE_COMPUTATIONS a été spécifié ou non). La signature empêche les valeurs signées d’être altérées par des utilisateurs non autorisés. Un pilote client compatible prenant en charge Always Encrypted peut vérifier la signature et retourner une erreur à l’application si la signature n’est pas valide. La signature doit être générée à l’aide d’outils côté client. Pour plus d’informations, consultez [Always Encrypted avec enclaves sécurisées](../../relational-databases/security/encryption/always-encrypted-enclaves.md).
  
  
## <a name="remarks"></a>Notes   

La création d’une entrée de métadonnées de clé principale de colonne est obligatoire avant qu’une entrée de métadonnées de clé de chiffrement de colonne puisse être créée dans la base de données et avant que toute colonne dans la base de données puisse être chiffrée à l’aide d’Always Encrypted. Notez qu’une entrée de clé principale de colonne dans les métadonnées ne contient pas la clé principale de colonne proprement dite, qui doit être stockée dans un magasin de clés de colonne externe (en dehors de SQL Server). Le nom du fournisseur de magasin de clés et le chemin de la clé principale de colonne dans les métadonnées doivent être valides pour qu’une application cliente puisse utiliser la clé principale de colonne pour déchiffrer une clé de chiffrement de colonne chiffrée avec la clé principale de colonne et pour interroger des colonnes chiffrées.


  
## <a name="permissions"></a>Permissions  
 Nécessite l’autorisation **ALTER ANY COLUMN MASTER KEY**.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-column-master-key"></a>A. Création d’une clé principale de colonne  
 Création d’une entrée de métadonnées de clé principale de colonne pour une clé principale de colonne stockée dans le magasin de certificats, pour des applications clientes qui utilisent le fournisseur MSSQL_CERTIFICATE_STORE afin d’accéder à la clé principale de colonne :  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
   );  
```  
  
 Création d’une entrée de métadonnées de clé principale de colonne pour une clé principale de colonne accessible par des applications clientes qui utilisent le fournisseur MSSQL_CNG_STORE :  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CNG_STORE',    
    KEY_PATH = N'My HSM CNG Provider/AlwaysEncryptedKey'  
);  
```  
  
 Création d’une entrée de métadonnées de clé principale de colonne pour une clé principale de colonne stockée dans le coffre de clés Azure, pour les applications clientes qui utilisent le fournisseur AZURE_KEY_VAULT afin d’accéder à la clé principale de colonne.  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/  
        MyCMK/4c05f1a41b12488f9cba2ea964b6a700');  
```  
  
 Création d’une entrée de métadonnées de clé principale de colonne pour une clé principale de colonne stockée dans un magasin de clés principales de colonne personnalisé :  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = 'CUSTOM_KEY_STORE',    
    KEY_PATH = 'https://contoso.vault/sales_db_tce_key'  
);  
```  
### <a name="b-creating-an-enclave-enabled-column-master-key"></a>B. Création d’une clé principale de colonne prenant en charge les enclaves  
 Création d’une entrée de métadonnées de clé principale de colonne pour une clé principale de colonne prenant en charge les enclaves stockée dans le magasin de certificats, pour des applications clientes qui utilisent le fournisseur MSSQL_CERTIFICATE_STORE afin d’accéder à la clé principale de colonne :  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
     KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',   
     KEY_PATH = 'Current User/Personal/f2260f28d909d21c642a3d8e0b45a830e79a1420'  
     ENCLAVE_COMPUTATIONS (SIGNATURE = 0xA80F5B123F5E092FFBD6014FC2226D792746468C901D9404938E9F5A0972F38DADBC9FCBA94D9E740F3339754991B6CE26543DEB0D094D8A2FFE8B43F0C7061A1FFF65E30FDDF39A1B954F5BA206AAC3260B0657232020542419990261D878318CC38EF4E853970ED69A8D4A306693B8659AAC1C4E4109DE5EB148FD0E1FDBBC32F002C1D8199D313227AD689279D8DEEF91064DF122C19C3767C463723AB663A6F8412AE17E745922C0E3A257EAEF215532588ACCBD440A03C7BC100A38BD0609A119E1EF7C5C6F1B086C68AB8873DBC6487B270340E868F9203661AFF0492CEC436ABF7C4713CE64E38CF66C794B55636BFA55E5B6554AF570CF73F1BE1DBD)
  );  
```  
  
 Création d’une entrée de métadonnées de clé principale de colonne pour une clé principale de colonne prenant en charge les enclaves stockée dans le coffre de clés Azure, pour les applications clientes qui utilisent le fournisseur AZURE_KEY_VAULT afin d’accéder à la clé principale de colonne.  
  
```  
CREATE COLUMN MASTER KEY MyCMK  
WITH (  
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',  
    KEY_PATH = N'https://myvault.vault.azure.net:443/keys/MyCMK/4c05f1a41b12488f9cba2ea964b6a700');
    ENCLAVE_COMPUTATIONS (SIGNATURE = 0xA80F5B123F5E092FFBD6014FC2226D792746468C901D9404938E9F5A0972F38DADBC9FCBA94D9E740F3339754991B6CE26543DEB0D094D8A2FFE8B43F0C7061A1FFF65E30FDDF39A1B954F5BA206AAC3260B0657232020582413990261D878318CC38EF4E853970ED69A8D4A306693B8659AAC1C4E4109DE5EB148FD0E1FDBBC32F002C1D8199D313227AD689279D8DEEF91064DF122C19C3767C463723AB663A6F8412AE17E745922C0E3A257EAEF215532588ACCBD440A03C7BC100A38BD0609A119E1EF7C5C6F1B086C68AB8873DBC6487B270340E868F9203661AFF0492CEC436ABF7C4713CE64E38CF66C794B55636BFA55E5B6554AF570CF73F1BE1DBD)
  );
```  
  
## <a name="see-also"></a> Voir aussi
 
* [DROP COLUMN MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-master-key-transact-sql.md)   
* [CREATE COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-column-encryption-key-transact-sql.md)
* [sys.column_master_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
* [Always Encrypted &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
* [Vue d’ensemble de la gestion des clés pour Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
  
