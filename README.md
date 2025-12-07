# GlobalVillageProject 
地球村计划
Earth Village is an open, collaborative project for all of humanity. We invite individuals, communities, developers, researchers, and businesses worldwide to participate in the design, auditing, and continuous iteration of this decentralized social system.  It uses decentralized identities (DID/VC) as the foundation for public identity, with identity-sensitive information encrypted at the field level using independent encryption and protected by post-quantum cryptography for long-term security. This ensures that while identities are verifiable and valid across the entire network, no one can access personal private information without the individual's authorization.

At the asset and housing level, real estate is bound and authenticated only through encrypted addresses/commitment values: the status and change records of properties are publicly accessible worldwide, but it's impossible to deduce ownership from the public registry. Transactions are completed in a verifiable but anonymous manner within a rule-bound witnessing process. Commercial assets are only available for lease, not purchase: rent automatically flows back and is equally distributed among residents in the surrounding area.  Businesses also contribute a fixed percentage (e.g., 5%) to the construction of public goods such as roads and public facilities, ensuring that value returns to the community in the long term.

The governance and execution layers employ a mechanism of "transparent rules, auditable processes, and revocable power": AI is used only as an auxiliary tool (for proposal organization, risk warning, and execution verification), and is constrained by clearly defined public principles and human oversight. This ensures that the system always prioritizes human dignity, freedom, and rights, and prevents any individual, organization, group, or single AI entity from gaining absolute control over others or the system, both institutionally and technologically.


#
Identity Encryption System – "Globally Verifiable Existence, but Unreadable Without the Owner's Authorization"

The Earth Village identity system is not based on national identification documents, but rather on a combination of "Decentralized Identity (DID) + Private Encrypted Vault + Verifiable Credentials (VC/VP)". The core objective of the system is: the entire world can verify whether an identity is real and valid, whether it has been revoked, and whether it possesses certain qualifications; however, no one (including site staff/security personnel/platforms) can read the individual's private content without the owner's authorization key.

1) Public Layer: DID (Publicly Verifiable "Identity Address," supporting updates/deactivation)

Each Earth Village member has one or more DIDs (Decentralized Identifiers), serving as publicly resolvable identity addresses. The DID design allows identifiers and DID documents to be created, verified, updated, and deactivated.

Address rotation: To prevent tracking, members can use "relationship-based/scenario-based DIDs" (e.g., different DIDs for different institutions or scenarios), and switch to a new DID at any time; the outside world only sees "valid/invalid/update records," not the identity's private content.

Note: Methods like did:key, which "directly generate a DID from a public key," are inherently unsuitable for scenarios requiring "long-term identity + key rotation/recovery/deactivation"; long-term identities should use DID methods that support registry/update.

The public layer is recommended to only disclose these "meta-information" (excluding privacy):

did, status (active/revoked/deactivated), updated_at

Current set of verification public keys (or their commitment/fingerprint)

vault_root_hash (the hash root of the private vault, used for tamper-proof reconciliation, without disclosing content)

2) Private Layer: Field-Level Encrypted Vault (Each piece of information is individually encrypted, individually authorized, and individually updated)

Members' sensitive information (as you mentioned: DNA, blood type, meridian and vascular pathways, iris, fingerprints, photos, name/age/place of birth, and self-set passwords, etc.) are all stored in a personal private encrypted vault, and follow three mandatory rules:

Field-level independent encryption: Each field is encrypted with an independent data encryption key (DEK); updating one field does not affect other fields. Field-level authorization: Authorizing someone to view "a specific field" does not equate to authorizing them to view all information.

Revocable/Updatable: Any field can have its authorization revoked, re-encrypted, or its version upgraded independently.

Key point: The on-chain/public layer never stores plaintext biometric information, plaintext photos, or plaintext places of birth; it only stores hash roots and status.

3) Implementation principles of "quantum/post-quantum encryption": Using post-quantum cryptography (PQC) to protect long-term security

If your "quantum encryption" is to be practically implemented, the core should be post-quantum cryptography: using standardized post-quantum algorithms for "key encapsulation (encrypting keys)" and "digital signatures (non-repudiation of authorization and updates)".

FIPS 203 (ML-KEM): Used for encapsulating/distributing field keys (DEK), enhancing post-quantum capabilities.

FIPS 204 (ML-DSA)/FIPS 205 (SLH-DSA): Used for signing identity updates, authorizations, revocations, rotations, etc., making public records verifiable and tamper-proof.

The public ledger is searchable and records are verifiable, but without the subject's private key, no field content can be decrypted.

4) Proof Layer: Only proving necessary information (Selective Disclosure / Zero-Knowledge)

The identity system does not encourage "showing private information to others," but instead defaults to answering questions with "verifiable proofs":

When needing to prove "I am a member of the global community/I have passed a certain qualification/I am an adult," use **W3C Verifiable Credentials (VC)** and Verifiable Presentations (VP). VC v2.0 explicitly supports "disclosing only partial claims" and "zero-knowledge presentations."

Using **SD-JWT (Selective Disclosure JWT)**, you can disclose only necessary fields, keeping other fields hidden; SD-JWT has become an IETF standard RFC 9901.

For stronger privacy (more difficult to link), "zero-knowledge proof presentations" can be used (proving that conditions are met without exposing the original values).

5) How can biometric information be used to "confirm identity," but still prevent any verifier from seeing the biometric data? The principle of the global village is: biometric data is only used for "local unlocking keys," and is not uploaded, leaked, or handed over to verifiers.

Using WebAuthn/FIDO/Passkeys: After local unlocking on the device (fingerprint/face/PIN), the private key within the device signs the challenge; the verifier only verifies whether the signature is correct.

Biometric information protection should meet requirements such as "confidentiality, integrity, and renewability/revocability," which is also a core focus of ISO/IEC 24745:2022.

6) Address Update and Key Rotation – Anti-Tracking + Anti-Account Theft

To meet your requirements for "updatable addresses and updatable keys":

Address Rotation: Members can periodically or manually switch to a new DID (especially using different DIDs for different scenarios), reducing the ability of third parties to track them through fixed addresses over the long term.

Key Rotation: Members can rotate their identity control keys; rotation records can be publicly verified, but will not expose private fields. The DID system itself supports update/deactivation and other operational models.

Revocation and Recovery: A revocation and recovery mechanism must be provided (otherwise, losing a device would mean "identity death"). Lifecycle management and authenticator management are essential parts of a mature identity system.

7) No one can control anyone: How does the identity system "counter control"?

The identity encryption system reduces the possibility of "controlling others" through the following mechanisms, both institutionally and technologically:

Default Minimum Disclosure: Verification only receives "proof of validity," not full privacy data.

Decentralized Key Control: Keys are held by individuals; the public ledger can only verify signatures/status, and cannot decrypt on behalf of individuals.

Revocable and Rotatable: If a leak is suspected, revoke/rotate immediately, and the old authorization becomes invalid.

Biometric Data Does Not Leave the Device: The verification point will never see your raw biometric data, only that "you have completed the device signature."
