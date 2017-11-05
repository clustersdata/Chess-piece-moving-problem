# Chess-piece-moving-problem

Chess piece moving problem

[参考程序]

const

     n=3; {n<5}
     
type

    ss=string[2*n+1];
    
    ar=array[1..630]of ss;
    
var

   a:ar;
   
   f,z:array[1..630] of integer;
   
   i,j,k,m,h,t,k1:integer;
   
   s,d:ss;
   
   q:boolean;
   
procedure print (x:integer);

var t:array[1..100] of integer;

    y:integer;
    
begin

     y:=0;
     
     repeat
     
           y:=y+1;
           
           t[y]:=x;
           
           x:=f[x];
           
     until x=0;
     
     writeln(a[t[y]]:2*n+4);
     
     writeln(copy('-------------------------',1,2*n+5));
     
     for x:=2 to y do writeln(x-1:2,':',a[t[y+1-x]]);
     
end;

begin

     s:='_';d:='_';
     
     for i:=1 to n do begin
     
         s:='o'+s+'*';
         
         d:='*'+d+'o';
         
     end;
     
     a[1]:=s;f[1]:=0;z[1]:=n+1;
     
     q:=false;
     
     i:=1;j:=2; t:=0;
     
     repeat
     
       for h:=1 to 4 do begin
       
               k:=z[i];k1:=k;s:=a[i];
               
               case h of
               
                1:if k>1 then k1:=k-1;
                
                2:if k<(2*n+1) then k1:=k+1;
                
                3:if (k>2) and (s[k-1]<>s[k-2]) then  k1:=k-2;
                
                4:if (k<(2*n)) and(s[k+1]<>s[k+2]) then k1:=k+2;
                
               end;
               
           if k<>k1 then begin
           
              s[k]:=s[k1];s[k1]:='_';
              
              m:=1;
              
              while (a[m]<>s) and (m< j-1) do m:=m+1;
              
              if a[m] >>s then begin
              
                 a[j]:=s;f[j]:=i;z[j]:=k1;
                 
                 if s=d then begin
                 
                    print(j);
                    
                    q:=true;
                    
                 end;
                 
                 j:=j+1;
                 
              end;
             

 end;
 
     end; {end for}
     
     i:=i+1;
     
  until q or (i=j);
  
readln;

end.
