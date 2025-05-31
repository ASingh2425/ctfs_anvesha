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
