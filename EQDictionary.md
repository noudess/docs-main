### What is it?
EQDictionary is a collection of lookup references, accessed by specific namespaces and referenced by client or mob version.

References are tied back to the originating client definition..but, are available through an indexed lookup system.

The purpose of this system is to allow cyclic or minimum conditional evaluations in order to transform data.

### What can you do with it?
Simplifying coding methodology can change current standards from this:

`if (ClientVersion() >= EQEmu::versions::ClientVersion::SoF) { bank_slot_count = 24; }`

`else { bank_slot_count = 16; }`

`if (current_slot >= bank_slot_count) { return; }`

Or this:

`if (m_ClientBitmask & EQEmu::versions::maskSoFAndLater) { bank_slot_count = 24; }`

`else { bank_slot_count = 16; }`

`if (current_slot >= bank_slot_count) { return; }`

To this:

`if (current_slot >= m_inv.GetInv().GetLookup()->InventoryTypeSize.Bank) { return; }`

The first case requires that clients to be added in order of release.

The second case will allow clients to be added in any order..but, requires awkward manipulation of mask bits.

The EQDictionary (last) case does not require any special ordering of clients or manipulation of mask bits.

In fact, this system makes ClientVersion bitmask use obselete.