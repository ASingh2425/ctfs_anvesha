##EVEN RSA CAN BE BROKEN???
This challenge actually took a lot of my time. I was blindly trying to apply all the maths concepts I ever learnt. At last I used RSA Decoder for this one.
Input value of N, C and E and it gives the encrypted message. I am yet to learn how did that happen.


##transposition-trial
Now the first is three letter long..so "The" comes out to be the first word. Next on replacing random spaces with underscores we can decode the message..
"ehT": "The"
"fl_": "_fl"
"g_a": "ag_"
"s_i": "is_"
"icp": "pic"
"CTo": "oCT"
Now the hint suggested to divide the message into blocks of three..

I used the following code for that:
def main():
    f = open("message.txt", "r", encoding="UTF-8")
    txt = f.read()

    n=3
    txt3gram = [txt[i:i+n] for i in range(0, len(txt), n)] //storing each substring in the list
    decode_lst = [] // empty list

    for i in range(len(txt3gram)):
        decode_lst.append(txt3gram[i][2]+txt3gram[i][0]+txt3gram[i][1]) //storing each substring by reversing it first and then appending it at last

    print(''.join(decode_lst))


if __name__ == '__main__':
    main()





##Hashcrack
i just got a few hash codes and i used online decoders to get the password and move forward
i got the flag eventually




##Dachshund Attacks
Connecting to nc mercury.picoctf.net 36463 in the webshell, it gives us the values of e, n and c
"Wiener RSA", we see that it's an attack method used on RSA, especially when "d" is too small 

import owiener

c = 51729254814612320597643328450085959536599727372680938760771949307679773005615308695648114596258975136775968889388756216401496118257971113771919925769604554578645725822883285841825381936016630539284003180253228150727414300152034618534378132051795168049160397854013369582290350212981743918731826059625571659195
e = 26708677238429428374170262208931535733743911260604248499407092969454401069520229604707421630650361943655516583033522359546446670546154254638564481680864845797555129549483370241281955795119447253220108830835178572671949509316867647933241089013588496517578768012481040939437738400995777121296915356470885241301
n = 102050270322368919270668432655276557677924971440195120212230040263372875358539516722287129116966588442412373177849929844163493405962383401732877189240511737479294203917101072408029656805628085793609392233931279848866908950627490592662932946058562223278970874388262808195065269805169207346022676107536878090839
d = owiener.attack(e, n)

if d is None:
    print("Failed")

else :
    print("Hacked d = {}".format(d))

this is the program i wrote

M = pow(c, d, n)

print("Decrypted message: ", M)

first number needs to be converted to hex and hex to plain text and we get the flag
