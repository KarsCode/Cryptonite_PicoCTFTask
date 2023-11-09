### substitution0
We are given the following message with a key used for substitution at the top: 

![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/541fe612-8af0-4ad6-8b9c-70f9c48aaebc)



Looking at the flag format it is understood that A is mapped to Z, B is mapped to G and so on. I created the following python code to decode the given substitution cipher. 


```python
ciphertext = "Qctcnrel Mcptzlo ztebc, fuwq z ptzac zlo bwzwcmd zut, zlo gtenpqw ic wqc gccwmcxtei z pmzbb szbc ul fqusq uw fzb clsmebco. Uw fzb z gcznwuxnm bsztzgzcnb, zlo, zwwqzw wuic, nlhlefl we lzwntzmubwb—ex sentbc z ptczw rtukc ul z bsuclwuxus reulwex aucf. Wqctc fctc wfe tenlo gmzsh brewb lczt elc cjwtciuwd ex wqc gzsh, zlo zmelp elc lczt wqc ewqct. Wqc bszmcb fctc cjsccoulpmd qzto zlo pmebbd, fuwq zmm wqczrrcztzlsc ex gntlubqco pemo. Wqc fcupqw ex wqc ulbcsw fzb actd tcizthzgmc, zlo,wzhulp zmm wqulpb ulwe selbuoctzwuel, U senmo qztomd gmzic Ynruwct xet qub erulueltcbrcswulp uw.Wqc xmzp ub: ruseSWX{5NG5717N710L_3A0MN710L_357GX9XX}"
key = "ZGSOCXPQUYHMILERVTBWNAFJDK"
decryption_dict = {key[i]: chr(65 + i) for i in range(26)}

decrypted_text = ""
for char in ciphertext:
    if char.isalpha():
        decrypted_text += decryption_dict.get(char.upper(), char).lower() if char.islower() else decryption_dict.get(char, char)

    else:
        decrypted_text += char

print("Decrypted Text:", decrypted_text)

```

![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/997e9bbb-2bbf-479b-8db2-1f598d8e78b0)
