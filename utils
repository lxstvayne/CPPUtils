#pragma once
#include <vector>
#include <string>
#include <iostream>
#include <cassert>


class InputStream
{
public:
    InputStream& read_while_not(const std::string __symbol) {
        if (__read_next() == __symbol) {
            __eof = true;
        }
        else {
            __eof = false;
        }
        
        return *this;
    }

    InputStream& read_n_times(const int __count) {
        assert(__count > 0);
        static int __current_count = 0;
        if (__count - __current_count > 0) {
            __read_next();
            __eof = false;
            __current_count++;
        }
        else {
            __eof = true;
            __current_count = 0;
        }
        return *this;
    }

    friend InputStream& operator>> (InputStream& is, std::string& s)
    {
        s = is.__get_last_value();
        return is;
    }

    operator bool() {
        return not __eof;
    }

private:
    std::string __last_value;
    bool __eof;

    std::string __get_last_value() {
        return __last_value;
    }

    std::string& __read_next() {
        getline(std::cin, __last_value);
        return __last_value;
    }

};

